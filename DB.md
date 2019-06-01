create database student   --- 创建数据库

dbo ----- 系统默认架构

# 2、关系代数

没有使用。。。。用整体-有的

至少有或者查询全部 用÷

# 第三章、关系数据库标准语言

学生表：Student(Sno,Sname,Ssex,Sage,Sdept)

课程表：Course（Cno,Cname,Cpno,Ccredit）

学生选课表：SC(Sno,Cno,Grade)

```sql
--常用的完整性约束
	--主码约束 primary key
	--唯一性约束 unique
	--非空值约束 not null
	--参照完整性约束 foreign key(参照) references 参照表(被参照列)
--**********创建数据库*******************************************
create database student
--使用数据库
use student
--创建模式
create schema s_t
--创建student表
create table student(
	Sno char(9) primary, --主键 列级完整性约束条件
    Sname varchar(20) unique,--Sname取值唯一
    Ssex char(2),
    Sage smallint,
    Sdept char(20)
);
--创建course表
create table course(
	Cno char(4) primary key,--主码
    Cname char(40),
    Cpno char(4),
    Ccredit smallint,
    foreign key(Cpno) references course(Cno)
    --Cpno是外码，被参照表是course表，被参照列是Cno
    --声明外键只能在最后声明
);
--创建sc表
create table sc(
	Sno char(9),
    Cno char(4),
    Grade smallint,
    primary key(Sno,Cno),
    --两个主码联合在一起的，只能在所有字段声明之后声明
    foreign key(Sno) references student(Sno),
    foreign key(Cno) references course(Cnp)
);
--删除数据库
drop database student

--************修改基本表*****************************************
--修改表的基本操作
	--add 用于添加新列、新的约束条件
	--alter column 用于修改原有列的列定义、数据类型
	--drop column 用于删除表中的列
	--drop table
		--restrict 删除表是有限制的，不能被其他表的约束条件所引用，如果有约束条件此表不能被删除
		--cascade 删除该表没有限制
--添加列(student表中添加一列入学时	间，类型是date型)
alter table student add s_entrace date
--修改数据类型
alter table student alert column Sage int
--添加唯一约束的条件
alter table course add unique(Cname)
--删除基本表
drop table student
                                                                                                                                                                                 

--*************建立索引*****************************************
--asc 升序
--desc 降序 含有空值，空值是最大值
--创建索引
create unique index stusno on student(sno asc)
create index coucon on course(cno desc)
--创建聚集索引，一个表中聚集索引只能有一个
create clustered index stu on student(sno asc)
--删除索引
drop index course.coucon --删除不成功是由于唯一约束生成的，应该先解除唯一约束条件
--建立聚集索引cluster
create clustered index coucname on course(cname)

--**************数据查询****************************************
--基本语法
	--select 列出查询的结果
	--from 指明访问对象
	--where 指定查询的条件
	--group by 将查询结果按指定字段取值分组
	--having 筛选出满足指定条件的组
	--order by 按指定的值，升降序排序查询结果
--************1、单表查询**********************
--查询全体学生的学号、姓名
select sno,sname
from student 
--查询全体学生的详细记录
select *
from student 
--查询每个学生的学号，出生年份  +上别名
select sno 学号,2019-sage 出生年份
from student
--消除不重复的行   distinct
select distinct sno
from sc
--查询满足条件的元祖where*********************************
--where语句后面不能出现聚集函数*******
	--比较      =，>=,<=,==,!=
	--确定范围   between and ，not between and
	--确定集合   in ， not in（in相当于多个or的缩写  ）
	--字符匹配   like， not like
	--空值      is null，is not null
	--多重条件   and ，or ， not
--通配符% ：表示任意多个（包含0个），_表示唯一 一个。
--转义符：可以随机设置，但最好用\，表示，用escape声明转译字符
--查询以'DB_'开头的，且倒数第三个字符为i的课程
select sdept
from student
where like 'DB|_%i___' escape "|"
--
select sno
from sc
where grade>60
--查找CS和IS的所有学生
select sno,sname,sdept
from student
where sdept in('CS','IS') --设置一个集合
--like定义模糊的东西
select sno,sname,sage
from student 
where like '李%'
--查询年龄为空的同学
select sno,sname,sage
from student
where sage is null-----------考试经常有
--查询课程名以‘数’开头的所有课程的课程名、学分
select cname,ccredit
from course
where cname like '数%'
--查询计算机系所有小于20岁的女生的学号、姓名
select sno,sname
from student
where sdept='CS' and ssex='女' and sage<20
--order by*******************************************
--查询选修3号课程的学生的学号及其成绩，查询结果按分数降序排序
select sno,grade
from sc
where cno='3'
order by desc
--查询全体学生情况，查询结果按所在系升序排序，同系学生按年龄降序
select *
from student
order by sdept,sage desc
--聚集函数*********************************************
--聚集函数（5个）
	--count（*）   统计元组个数
	--avg()       计算平均值
	--sum()       计算总和
	--max()       求最大值
	--min()       求最小值
	--不添加distinct表示不取消重复值***
--查询选修了课程的学生人数
select count(distinct sno)
from sc
--计算1号课程的学生平均成绩
select avg(grade)
from sc
where cno='1'
--group by*******************************************
--未对查询结果分组，聚集函数面向整个查询结果
--对查询结果分组后，聚集函数分别作用于每个组
----------****************-----------
使用group by子句，select子句的列表只能出现分组属性和聚集函数
where语句不能出现聚集函数
可以使用having短语筛选最终结果
----------****************-----------
--查询各个课程号及相应的选课人数
select cno,count(sno)
from sc
group by cno
--查询选修了3门课程以上的学生学号
select sno
from sc
group by cno
having count(*)>3
--having作用于组，where作用于基表或试图
--******************连接查询************************************
--连接运算符为 = 时，称为等值连接，等值连接中去掉目标列的重复属性则为自然连接
--其他运算符为非等值连接
--查询每个学生及其选修课程的情况
select student.*,sc.*
from student,sc
where studet.sno = sc.sno
--自身连接 ，自己与自己连接，一般起别名
--查询每一门可定间接先修课
select first.cno,second.cpno
from course first,course second
where first.cpno = second.cno
--外连接(一般***没有也包括就用外连接)******************************
--外连接 full outer join 
--左外链接 left outer join
--右外连接 right outer join
--查询每个学生及其选修课的情况，包括没有选修课程的学生
select student.sno,sname,sdept,cno,grade
from student left outer join sc
on student.sno=sc.sno
--嵌套查询******************************************************
--子查询不能使用order by
--不相关子查询
	子查询的查询条件不依赖于父查询（有里向外查询，子查询为父查询提供条件）
--相关子查询
	子查询的查询条件依赖于父查询（外层提供查询条件）
/*带有in谓词的子查询*/
--查询和‘刘晨’一个系的学生
select sname
from student
where sdept in(
	select sdept
    from student
    where sname='刘晨'
)
--查询选修了课程名为‘信息系统’的学生学号和姓名（从内向外推）
select sno,sname
from student
where sdept in(
	select sno
    from sc
    where cno in(
    	select cno
        from course
        where cname='信息系统'
    )
)
/*带有比较运算符的子查询*/

--找出每个学生超过他选修课程平均成绩的课程号
select cno
from student x
where grade>=(
	select avg(grade)
    from student y
    where x.sno = y.sno
)
/*any 任意一个 <（>）any 小于某一个值（大于某一个值）
 *all 所有值	<（>）all 小于所有值（大于最大值）
 */
 --查询其他系中比信息系任意一个学生年龄小的学生姓名和年龄
 select sname,sage
 from student
 where sage <any(
 	select sage
    from student
    where sdept='IS'
 )
 and sdept != 'IS'
 --查询其他系中比计算机科学系所有学生年龄小的学生姓名和年龄
 select sname,sage
 from student
 where sage <all(
 	select sage
     from student
     where sdept = 'CS'
 )and sdept != 'CS'
/*带有exists谓词的子查询*/

--带有exists谓词的子查询不返回任何数据，只产生逻辑真值
	若内层查询非空，则外层的where子句返回真值
	若内层查询为空，则外层的where子句返回false
--not exists
	若内层查询非空，则外层的where子句返回false
	若内层查询为空，则外层的where子句返回true
--用exists查询子查询中的select后都是*
--查询所有先修了1号课程的学生姓名
select sname
from student
where exists
	(select *
   	 from sc
     where cno = '1' and student.sno = sc.sno
    )
--查询没有选修1号课程的学生姓名
select sname
from student
where not exists
	(select *
     from sc
     where student.sno = sc.sno and cno='1'
    )
--查询选修了全部课程的学生姓名（没有课程没有学生不选）
select sname
from student
where not exists
	(
        select *
     	from course
     	where not exists
     	(
            select *
         	from sc
         	where sc.sno = student.sc and 
         		sc.cno = course.cno
        )
    )
--查询至少选修了学生201215122选修的全部课程的学生学号
select distinc sno
from sc x
where not exists
(
	select *
    from sc y
    where y.sno ='201215122' and
    not exists
    (
    	select *
        from sc z
        where z.sno=x.sno
        and z.cno = y.cno
    )
)

```

# 第六章

## 6.1、函数依赖

​	函数依赖是一个关系内部属性与属性之间的一种约束关系。分为函数依赖FD和多值依赖MVD

## 6.2、规范化

设R(U)是一个属性集U上的关系模式，X和Y是U的子集若对于R(U)的任意一个可能的关系r，r中不可能存在两个元组在X上的属性值相等， 而在Y上的属性值不等， 则称 “X函数确定Y 或  “Y函数依赖于X**”，**记作X→Y。

   **X**称为这个函数依赖的**决定属性集**(Determinant)。

# 第八章

```sql
declare @var1 char(10),@var2 datetime
set @var2=GETDATE()
set @var1=convert(char(10),@var2)
--全局变量 @@开头
print @@VERSION--显示当前文本
print @@SERVERNAME--显示服务器名称
print @@servicename--显示目前所用服务器

--查找201215121的学生
if exists(select * from student where sno='201215121')
	begin
		select *
		from student
		where sno='201215121'
	end
else
	print '没找到'
	
```

2019/05/15

```sql
begin
    waitfor delay '00:00:05' --(或者换成time '00:52:15'具体的时间)
        select *
        from student
end
--数据类型装换

--游标

```

## 第一节:T-SQL编程基础

**1.标识符:**（**空格是什么。**。）

​	字母或_、@、# 开头的字母数字或 _、@、$序列

​	不与保留字相同

​	长度小于128

​	不符合规则的标识符需要加以界定(双引号“ ”，或方括号[])

**2.变量**

​	局部变量：用户定义，必须以@开头，在程序内部声明，并且只能在程序内部使用。

​	局部变量声明：declare @<变量名> <数据类型> ====> declare @num int

​	局部变量赋值：set |select @<变量名> = <表达式> ====> set @num = 1

set赋值：一次只能赋值一个变量

select赋值：一次赋值多个变量 select @a=1,@b=2....

select也可以输出，select @a;或者print @a

**3.类型转换**

​	convert(char(2),@a)

**4.全局变量**

​	全局变量：以@@开头，不由用户定义，服务器定义的。

**5.控制流程语句**

```SQL
--1、选择结构
--(1)、if ....else
--查找有没有学号为201215121的学生，有的话显示学生信息，没有显示没找到
if exists(select * from student where sno='201215121')
begin
	select *
	from student
	where sno='201215121'
end
else
	print '没有找到'
--(2)、case语句
--从学生表student中，选取sno，ssex，如果ssex为男，则输出M，如果为女则输出F
select sno,ssex=
	case ssex
	when '男' then 'M'
	when '女' then 'F'
	end
from student
--(3)、搜索式case
--从SC表中查询所有同学选课成绩情况，凡成绩为空者输出‘未考’、小于60输出‘不及格’ 、小于70输出‘及格’ 、小于90输出‘良好’ 、大于等于90输出‘优秀’ 
select sno,cno,grade=
	case grade
		when grade is null then '未考'
		when grade<60 then '不及格'
		when grade>=60 and grade<70 then '及格'
		when grade>=70 and grade<90 then '良好'
		when grade>=90 then '优秀'
	end
from sc

--2、循环结构
--求1-10的和
declare @a int ,@sum int
set @a=1
set @sum=0
while(@a<=10)
	begin 
		set @sum = @sum +@a
		set @a=@a+1
	end
print 'sum=' +convert(char(2),@sum) --类型转换函数
--等待语句
	waitfor delay '<时间间隔>'|time '<时间>'
	--时间间隔及时间均为datetime类型，格式为'hh:mm:ss'
	waitfor delay "00:00:02"
	begin
    	select *
    	from student
	end
--返回语句
	--return语句用于无条件的终止一个查询、存储过程或者批处理。
--日期和时间函数
select '年龄'=
	datediff(YY,'1999-12-07',getdate())
--返回指定日期中的年/月/日的整数
select year('2019-05-22');

--数据类型转换
select sno+sname+cast(sage as char(2))
from student

select sno+sname+convert(char(2),sage)
from student

```



## 第二节：游标

游标是一种能从包括多条数据记录的结果集中每次提取一条记录的机制

```sql
--统计没有选课程的学生的人数
--1、声明游标
declare num_cursor cursor 
for
	select sno
	from student
for read only
--2、打开游标
open num_cursor
--3、读取游标中的数据
--fetch (默认指针指向第一条记录之前)
--next :返回结果的当前行的下一行
--prior：但会当前结果的前一行
--first：返回游标中的首个记录
--last：返回游标中的最后一个记录
--absolute：是绝对位置，他将指针移到第n行位置
--relative：如果n是正数则为当前位置之后的第n歌位置，为负则为当前位置向前            的第n个位置
--into：允许将使用fetch语句读取的数据存放在若干个局部变量中，在变量行中的         每个变量必须与游标结果集中相应的列相对应。
--执行fetch语句后，可通过@@fetch_status全局变量返回游标当前的状态。
--@@fetch_status =0 ：fetch语句执行成功
               --=-1：fetch语句指向失败或数据超出范围
               --=-2：提取数据不存在
declare @sno varchar(9),@num int 
set @num=0
fetch next from num_cursor into @sno
while @@fetch_status=0
begin
	if not exists(select * from student where sno=@sno)
       set @num = @num+1
    fetch next from  num_fetch into @sno
end
select @num
--4、关闭游标
close num_cursor
--5、释放游标
deallocate num_cursor

--根据学生成绩计算各个等级的人数
declare level_cursor cursor
for 
	select grade from sc
for read only

open level_cursor

declare @a int,@b int,@c int,@d int,@e int,@mygeade int
select @a=0,@b=0,@d=0,@c=0,@e=0
fetch next from level_cursor into @mygrade
while @@fetch_status=0
begin
	if @mygrade is null
		set @e=@e+1
	else if @mygrade <60
		set @e = @e+1
	else if @mygrade<=70 and @mygrade>=60
		set @d=@d+1
	else if @mygrade<80 and @mygrade>=70
		set @c=@c+1
	else if @mygrade<90 and @mygrade>=80
		set @b=@b+1
	else if @mygrade>900
		set @a=@a+1
	fetch next from level_cursor into @mygrade
end
select @a 优秀,@b 良好,@c 中等,@d 一般,@e 不及格
close level_cursor
deallocate level_cursor
```

## 第三节：存储过程

​	存储过程是一组完成特定功能的SQL语句集，经编译后存储在数据库中，用户通过指定存储过程的名字并给出参数（如果该存储过程带有参数）来执行存储过程。

```sql
--1、 创建存储过程
--从sc中查询不及格课程超过三门的学生信息 *******没有参数
create proc num
as
select *
from student
where son in(
	select sno
    from sc
    where grade<60
    groun by sno
    having count(sno)>3
)
--将指定记录插入到student表  ********************有参数
create proc proc_insert_student
@sno varchar(10),
@sname varchar(20),
@ssex char(2)='男',--*********设置默认值
@sage smallint,
@sdept varchar(5)
as
begin
	insert into student(sno,sname,ssex,sage,sdept)
	values(@sno,@sname,@ssex,@sage,@sdept)
end
exec proc_insert_student('')
--查询指定学号学生的平均成绩，并将成绩返回
create proc mygrade
@sno varchar(10),
@grade int out  -- *********************************设置输出型参数
as
begin 
	select grade
	from sc
	where sno=@sno
end

declare @sn int(10)
set @sn=0
exec mygrade '201215129',@sn out
select @sn

--请编写一个存储过程proc_sum，输入参数为学院，输出参数为人数，功能为根据输入的学院，统计该学院的学生人数，并返回学生人数。学生表的结构为（sno,sname,sex,department）各个字段含义为学号、姓名、性别、学院
create proc proc_num
@sdept varchar(5),
@num int out
as
begin 
	select @num=count(sno)
	from student
	where sdept=@sdept
end

declare @num int
set @num =0
exec proc_num 'CS',@num out
select @num
--2、执行存储过程
declare @num int
set @num =0
exec proc_num 'CS',@num out
select @num

--3、删除存储过程
drop proc proc_num
```

## 第四节：自定义函数

标量函数返回一个标量(单值)结果

内嵌表值函数返回一个table数据类型

多语句表值函数返回的数据必须存放于临时表中（性能不好）

```sql
--1、标量函数
--标量函数返回一个标量的结果
--定义一个函数返回不带时间的日期
create function dateonly(@date datetime)
returns varchar(12) --returns设置返回值类型
as
begin
	return convert(varchar(12),@date,102)--这里为什么是102
	--return设置返回值
end
print dbo.dateonly(getdate())

--
create function whichgeneration(@date datetime)
returns varchar(10)
as
begin 
	if year(@date)<1980
		return 'too old'
	else if year(@date)<1990
		return '80s'
	else
		return '90s'
	return ''--******************************
end

print dbo.whichgeneration('1999-12-07')

--2、内嵌表值函数

create function fun1()
returns table 
as
return select sno,sname
		from student
select *
from fun1()
		
--create function grade()
--returns table
--as
--return select avg(grade) '计算机系平均成绩'
--		from student,sc
--		where sdept='CS' and student.sno=sc.sno
		
--select *
--from grade()

```

## 第五节：触发器

```sql
--1、insert触发器
create trigger tr_sc_grade
on sc
after inster
as
begin
	declare @score smallint
	select rroe@score=grade from inserted
	if(@score>100 or @score<0)
		begin
			raiserror('成绩必须在0和100之间',10,1)
			--delete from sc where grade=@score
			rollback transaction --回滚事务
		end
end


--2、update触发器
create trigger tr_student_update
on student
for update
as
begin
	select * 
	from insterted
end

update student
set sname='pcy'
where sname='hhh'

--3、delete触发器
create table s1
(
	sno char(9),
    sname char(9)
    grade smallint
);
create trigger tr_sc-delete
on sc
for delete
as
begin
	inster into s1
	select *
	from deleted
end


```



```sql
--1、
create function funbook(@类别名 char(9))
returns table
as
	return 
		select 图书.* 
		from 图书,图书类别
		where 图书.类别编号 = 图书类型.类别编号 and 图书类型.类比名=@类别名

--2、
create trigger TrInsUpd
on 图书
for insert,update
as
begin
	declare @类别编号 char(9)
	select @类别编号=类别编号
	from inserted
	if not exists(select * from 图书类别 where 类别编号=@类别编号 )
        begin 
        	raiserror('图书类别号不存在')
        	rollback transaction
        end
end
```


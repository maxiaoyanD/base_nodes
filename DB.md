create database student   --- 创建数据库

dbo ----- 系统默认架构

# 2、关系代数

没有使用。。。。用整体-有的

至少有或者查询全部 用÷

# 3、关系数据库标准语言

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

第八章

```sql
declare @var1 char(10),@var2 datetime
set @var2=GETDATE()
set @var1=convert(char(10),@var2)

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


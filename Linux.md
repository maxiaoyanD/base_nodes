sudo：可以获取用户权限

设置root密码：sudo passwd root

切换到root用户：su + root刚设置的密码

创建普通用户：adduser +创建名（没有权限在前面加sudo）

创建用户组：sudo addgroup h5

创建用户指定用户组：sudo adduser   -- ingroup 组名 用户名

删除用户：sudo deluser + 名称

删除组：sudo delgroup + 组名





sudo mkdir /phy_share/leonard

sudo mkdir /phy_share/sheldon

ll /phy_share/

sudo chown leonard:physics /phy_share





3.sudo 







nano

配置：sudo nano /etc/nanorc














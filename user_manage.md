# Linux使用者管理

### Linux账号和用户组
>  用户标识符：UID GID  
 ```shell script
root@instance-e4y21hmd:~# id root
uid=0(root) gid=0(root) groups=0(root)
root@instance-e4y21hmd:~# id melon
uid=1000(melon) gid=1000(melon) groups=1000(melon)

# 所有用户记录存储在/etc/passwd
```

> 用户账号  
```shell script
# 登录Linux过程

1. 使用tty1~tty6的终端提供的登录接口, 输入用户名和密码
2. 先在/etc/passwd中查找账号, 没有则退出, 有则一并读出UID  GID 家目录和Shell设置
3. 进入/etc/shadow找出对应账号和UID 核对密码
4. 一切ok则进入shell管理阶段
```

/etc/passwd 文件结构
```shell script
root@instance-e4y21hmd:~# head -n 4 /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin

# 账号名称
# 密码 密码数据改到/etc/shadow中
# UID
# GID  这个与/etc/group 有关
# 用户信息说明
# 家目录
# shell
```

/etc/shadow 文件格式
```shell script
root@instance-e4y21hmd:~# head -n 4 /etc/shadow
root:$6$sgjd5AFQkZcGwYTe$17EmAJsnuc0K.wIb9wpOxmohK4TJzBjBpM.GFjnjHoPnGFEA5HudMljrakaMm1R9ixLrFq4q3LOvzcSDaPzqo1:18045:0:99999:7:::
daemon:*:17737:0:99999:7:::
bin:*:17737:0:99999:7:::
sys:*:17737:0:99999:7:::

# 账号名称
# 密码
# 最近修改密码的日期
# 密码不可被修改的天数
# 密码需要重新修改的天数
等等等
```

> 用户组  

/etc/group 文件结构
```shell script
root@instance-e4y21hmd:~# head -n 4 /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:

# 组名
# 用户组密码
# GID
# 此用户组支持的账号名称

```

有效用户组
```shell script
# 初始用户组
/etc/passwd 里的GID就是初始用户组

# 第一个为有效用户组
root@instance-e4y21hmd:~# groups
root

# 有效用户组的切换
newgrp docker

```

/etc/gshadow 文件结构
```shell script
root@instance-e4y21hmd:~# cat /etc/gshadow
uuidd:!::
ssh:!::
ntp:!::
netdev:!::
docker:!::
melon:!::

# 组名
# 密码 ！表示无合法密码，所以无用户组管理员
# 用户组管理员账号
# 有加入该用户组支持的所属账号
```
### 账号管理


### 主机详细权限规划

### 用户身份切换

### 用户信息的传递

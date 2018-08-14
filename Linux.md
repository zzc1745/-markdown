# [Linux常用命令](https://www.cnblogs.com/wuzhao-code/p/6244424.html)

# 命令格式与目录处理命令 ls

```
命令格式与目录处理命令 ls
命令格式：命令 [-选项][参数]
        例：ls -la /etc
说明：
     1）个别命令使用不遵循格式
     2）当有多个选项时，可以写在一起
     3）简化选项与完整选项
           -a 等于 --all
```

# 目录处理命令 ls

```
命令名称：ls
命令因为原意：list
命令所在路径：/bin/ls
执行权限：所有用户
功能描述：显示目录文件
语法：ls 选项[-ald][文件或目录]
            -a 显示所有文件，包括隐藏文件
            -l 详细信息显示 
            -d 查看目录属性

-rw-r–r– 
文件类型（-文件 d目录 l软链接文件） 
rw- r– r– 
u g o 
u所有者 g所属组 o其他人 
r读 w写 x执行
```

# 目录处理命令

## 命令名称：mkdir

```
命令因为原意：make directories
命令所在路径：/bin/mkdir
执行权限：所有用户
执行权限：所有用户
功能描述：创建新目录
        -p 递归创建
```

1. `例：mkdir -p/tmp/japan/hanmeimei`
2. `mkdir /tmp/japan/lilei /tmp/japan/hanmeimei`

## 命令名称：cd

```
命令因为原意：change directory
命令所在路径：shell内置命令
执行权限：所有用户
语法：cd [目录名]
功能描述：切换目录
```

1. `例：cd /tmp/japan/hanmeimei 切换到指定目录`
2. `cd .. 回到上一级目录`

## 命令名称：pwd

```
命令因为原意：print working directory
命令所在路径：/bin/pwd
执行权限：所有用户
语法：pwd
功能描述：显示当前目录
```

1. `范例：$ pwd`

## 命令名称：rmdir

```
命令因为原意：remove empty directories
命令所在路径：/bin/rmdir
执行权限：所有用户
语法：rmdir [目录名]
功能描述：删除空目录
```

1. `范例：$ rmdir /tmp/japan/lilei`

## 命令名称：cp

```
命令因为原意：copy
命令所在路径：/bin/cp
执行权限：所有用户
语法:cp -rp [原文件或目录][目标目录]
        -r 复制目录
        -p 保存文件属性
功能描述：复制文件或目录
```

1. `范例：$ cp -r /tmp/japan/hanmeimei /root`
2. `将目录/tmp/japan/hanmeimei 复制到目录/root下`
3. ``
4. `cp -rp /tmp/japan/hameimei /tmp/japan/lilei /root`
5. `将/tmp/japan目录下的hanmeimei和lilei目录复制到root下，并保持目录属性`

## 命令名称：mv

```
命令因为原意：move
命令所在路径：/bin/mv
执行权限：所有用户
语法:mv [原文件或目录][目标目录]
功能描述：剪切文件、改名
```

## 命令名称：rm

```
命令因为原意：remove
命令所在路径：/bin/rm
执行权限：所有用户
语法:rm -rf[文件或目录]
        -r 删除目录
        -f 强制执行
功能描述：删除文件
```

1. `范例：$ rm /tmp/yum.log`
2. `删除文件/tmp/yum.log`
3. ``
4. `rm -rf /tmpjapan/lilei`
5. `删除目录/tmp/japan/lilei`

# 文件处理命令

## 命令名称：touch

```
命令所在路径：/bin/touch
执行权限：所有用户
语法:touch [文件名]
功能描述：创建空文件
```

1. `范例：$ touch log.log`

## 命令名称：cat

```
命令所在路径：/bin/cat
执行权限：所有用户
语法:cat [文件名]
功能描述：显示文件内容
            -n 显示行号
```

1. `范例：$ cat /etc/issue`
2. `cat -n /etc/services`

## 命令名称：tac

```
命令所在路径：/usr/bin/tac
执行权限：所有用户
语法:tac [文件名]
功能描述：显示文件内容(反向列示)
```

1. `范例：$ tac /etc/issue`

## 命令名称：more

```
命令所在路径：/bin/more
执行权限：所有用户
语法:more [文件名]
    (空格)或f  翻页
    (Enter)     换行
    q或Q     退出
功能描述：分页显示文件内容
```

1. `范例：$ more /etc/services`

## 命令名称：less

```
命令所在路径：/usr/bin/less
执行权限：所有用户
语法:less [文件名]
功能描述：分页显示文件内容(可向上翻页)
```

1. `范例：$ less /etc/services`

## 命令名称：head

```
命令所在路径：/usr/bin/head
执行权限：所有用户
语法:head [文件名]
功能描述：显示文件前面几行
        -n 指定行数
```

1. `范例：$ head -n 20 /etc/services`

## 命令名称：tail

```
命令所在路径：/usr/bin/tail
执行权限：所有用户
语法:tail [文件名]
功能描述：显示文件后面面几行
            -n 指定行数
            -f 动态显示文件末尾内容
```

1. `范例：$ tail -n 18 /etc/services`

## 命令名称：ln

```
命令英文原意：link
命令所在路径：/bin/link
执行权限：所有用户
语法:ls -s [原文件][目标文件]
            -s 创建软链接
功能描述：生成链接文件
```

1. `范例：$ ln -s /etc/issue /tmp/issue.soft`
2. `创建文件/etc/issue的软链接/tmp/issue.soft`
3. ``
4. `ln /etc/issue /tmp/issue.hard`
5. `创建文件/etc/issue的硬链接/tmp/issue.hard`

**软链接特征：类似Windows快捷方式** 
*1.1rwxrwxrwx 1软链接* 
*软链接文件权限都为rwxrwxrwx* 
*2、文件大小-只是符号链接* 
*3、/tmp/issue.soft->/etc/issue* 
*箭头指向原文件* 
**硬链接特征：** 
*1.拷贝cp -p + 同步更新* 
*echo "this is a test" >> /etc/motd* 
*2.可通过i节点识别* 
*3.不能跨分区* 
*4.不能针对目录使用*

 

# 权限管理命令

## 命令名称：chmod

```
命令英文原意：change the permissions mode of a file
命令所在路径：/bin/chmod
执行权限：所有用户
语法：chmod [{ugoa}{+-=}{rwx}] [文件或目录]
            [mode=421 ] [文件或目录]
            -R 递归修改 
功能描述：改变文件或目录权限
```

**权限的数字表示**

 

| 权限的数字表示 |      |
| -------------- | ---- |
| r              | 4    |
| w              | 2    |
| x              | 1    |

 

1. `范例：$ rwxrw-r--`
2. `7 6 4`
3. ``
4. `范例：$ chmod g+w testfile`
5. `赋予文件testfile所属组写权限`
6. `chmod -R 777 testdir`
7. `修改目录testfile及其目录下文件为所有用户具有全部权限`

![img](https://images2015.cnblogs.com/blog/1078094/201701/1078094-20170103122312706-1491432894.png)

 

其他权限命令

## 命令名称：chown

```
命令英文原意：change file ownership
命令所在路径：/bin/chown
执行权限：所有用户
语法：chown [用户] [文件或目录]
功能描述：改变文件或目录的所有者
```

1. `范例：$ chown hanmeimei beijian`
2. `改变文件beijian的所有者为hanmeimei`

## 命令名称：chgrp

```
命令英文原意：change file group ownership
命令所在路径：/bin/chgrp
执行权限：所有用户
语法：chgrp [用户组] [文件或目录]
功能描述：改变文件或目录的所属组
```

1. `范例：$ chgrp hmeimei beijing`
2. `改变文件beijing的所属组为hanmeimei`

## 命令名称：umask

```
命令英文原意：the user file-creation mask
命令所在路径：Shell内置命令
执行权限：所有用户
语法：umask [-S]
        -S 以rwx形式显示新建文件缺省权限
功能描述：显示、设置文件的缺省权限
```

1. `范例：$ umask -S`

 

# 文件搜索命令

## 命令名称：find

```
命令所在路径：/bin/find
执行权限：所有用户
语法：find [搜索范围] [匹配条件]
功能描述：文件搜索
```

1. `范例：$ find /etc -name init`
2. `在目录/etc中查找文件init`
3. `-iname 不区分大小写`
4. `find / -size +204800`
5. `在根目录下查找大于100MB的文件`
6. `+n 大于 -n 小于 n 等于`
7. `find /home -user hanmeimei`
8. `在根目录下查找所有者为hanmeimei的文件`
9. `-group 根据所属组查找`
10. `find /etc -cmin -5`
11. `在/etc下查找5分钟内被修改过属性的文件和目录`
12. ``
13. `-amin 访问时间 access`
14. `-cmin 文件属性 change`
15. `-mmin 文件内容 modify`
16. ``
17. `find /etc -size +163840 -a -size -204800`
18. `在/etc下查找大于80MB小于100MB的文件`
19. ``
20. `-a 两个条件同时满足`
21. `-o 两个条件满足任意一个即可`
22. ``
23. `find /etc -name inittab -exec ls -l {} \;`
24. `在/etc下查找inittab文件并显示其详细信息`
25. `-exec/-ok 命令 {} \; 对搜索结果执行操作`
26. ``
27. `-type 根据文件类型查找`
28. `f 文件 d 目录 l 软链接文件`
29. `-inum 根据i节点查找`

## 命令名称：locate

```
命令所在路径：/usr/bin/locate
执行权限：所有用户
语法：locate 文件名
功能描述：在文件资料库中查找文件
```

1. `范例：$ locate inittab`

## 命令名称：which

```
命令所在路径：/usr/bin/which
执行权限：所有用户
语法：which 命令
功能描述：搜索命令所在目录及别名信息
```

1. `范例：$ which ls`

## 命令名称：whereis

```
命令所在路径：/usr/bin/whereis
执行权限：所有用户
语法：whereis [命令名称]
功能描述：搜索命令所在目录及帮助文档路径
```

1. `范例：$ whereis ls`

## 命令名称：grep

```
命令所在路径：/bin/grep
执行权限：所有用户
语法：grep -iv [指定字串] [文件]
功能描述：在文件中搜寻字串匹配的行并输出
                    -i 不区分大小写
                    -v 排除指定字串
```

1. `范例：# grep mysql /root/install.log`

 

# 帮助命令

## 命令名称：man

```
命令英文原意：manual
命令所在路径：/usr/bin/man
执行权限：所有用户
语法：man [命令或配置文件]
功能描述：获得帮助信息
```

1. `范例： $ man ls`
2. `查看ls命令的帮助信息`
3. `$ man services`
4. `查看配置文件services的帮助信息`

## 命令名称：help

```
命令所在路径：Shell内置命令
执行权限：所有用户
语法：help 命令
功能描述：获得Shell内置命令的帮助信息
```

1. `范例： $ help umask`
2. `查看umask命令的帮助信息`

```
 
```

# 用户管理命令

## 命令名称：useradd

```
命令所在路径：/usr/sbin/useradd
执行权限：root
语法：useradd 用户名功能描述：添加新用户
功能描述：添加新用户
```

1. `范例： $ useradd lilei`

## 命令名称：passwd username

```
命令所在路径：/usr/bin/passwd
执行权限：所有用户
语法：passwd 用户名
功能描述：设置用户密码
```

1. `范例： $ passwd lilei`

## 命令名称：who

```
命令所在路径：/usr/bin/who
执行权限：所有用户
语法：who
功能描述：查看登录用户信息
```

1. `范例： $ who`

## 命令名称：w

```
命令所在路径：/usr/bin/w
执行权限：所有用户
语法：w
功能描述：查看登录用户详细信息
```

1. `范例： $ w`

 

# 压缩解压命令

## 命令名称：gzip(只能压缩文件，不能压缩目录)

```
命令英文原意：GNU zip
命令所在路径：/bin/gzip
执行权限：所有用户
语法：gzip [文件]
功能描述：压缩文件
压缩后文件格式：.gz
```

## 命令名称：gunzip(解压)

```
命令英文原意：GNU unzip
命令所在路径：/bin/gunzip
执行权限：所有用户
语法：gunzip [压缩文件]
功能描述：解压缩.gz的压缩文件
```

1. `范例： $ gunzip boduo.gz`

## 命令名称：tar

```
命令所在路径：/bin/tar
执行权限：所有用户
语法：tar 选项[-zcf] [压缩后文件名] [目录]
            -c 打包
            -v 显示详细信息
            -f 指定文件名
            -z 打包同时压缩
功能描述：打包目录
压缩后文件格式：.tar.gz
```

1. `范例：$ tar -zcf Japan.tar.gz Japan`
2. `将目录Japan打包并压缩为.tar.gz文件`

**tar命令解压缩语法:** 
*-x 解包* 
*-v 显示详细信息* 
*-f 指定解压文件* 
*-z 解压缩*

1. `范例：$ tar -zxvf Japan.tar.gz`

## 命令名称：zip

```
命令所在路径：/usr/bin/zip
执行权限：所有用户
语法：zip 选项[-r] [压缩后文件名] [文件或目录]
            -r 压缩目录
功能描述：压缩文件或目录
压缩后文件格式：.zip
```

1. `范例：$ zip buduo.zip boduo`
2. `压缩文件`
3. `$ zip -r Japan.zip Japan`
4. `压缩目录`

## 命令名称：unzip

```
命令所在路径：/usr/bin/unzip
执行权限：所有用户
语法：unzip [压缩文件]
功能描述：解压.zip的压缩文件
```

1. `范例：$ unzip test.zip`

## 命令名称：bzip2

```
命令所在路径：/usr/bin/bzip2
执行权限：所有用户
语法： bzip2 选项 [-k] [文件]
                  -k 产生压缩文件后保留原文件
功能描述：压缩文件
压缩后文件格式：.bz2
```

1. `范例：$ bzip2 -k boduo`
2. `$ tar -cjf Japan.tar.bz2 Japan`

## 命令名称：bunzip2

```
命令所在路径：/usr/bin/bunzip2
执行权限：所有用户
语法： bunzip2 选项 [-k] [压缩文件]
                    -k 解压缩后保留原文件
功能描述：解压缩
```

1. `范例：$ bunzip2 -k boduo.bz2`
2. `$ tar -xjf Japan.tar.bz2`

# 网络命令

## 指令名称：write

```
指令所在路径：/usr/bin/write
执行权限：所有用户
语法：write <用户名>
功能描述：给用户发信息，以Ctrl+D保存结束
```

1. `范例： # write linzhiling`

## 命令名称：ping

```
命令所在路径：/bin/ping
执行权限：所有用户
语法：ping 选项 IP地址
            -c 指定发送次数
功能描述：测试网络连通性
```

1. `范例： # ping 192.168.1.156`

## 命令名称：ifconfig

```
命令英文原意：interface configure
命令所在路径：/sbin/ifconfig
执行权限：root
语法：ifconfig 网卡名称 IP地址
功能描述：查看和设置网卡信息
```

1. `范例：# ifconfig eth0 192.168.8.250`

## 命令名称：mail

```
命令所在路径：/bin/mail
执行权限：所有用户
语法：mail [用户名]
功能描述：查看发送电子邮件
```

1. `范例：# mail root`

## 命令名称：last

```
命令所在路径：/usr/bin/last
执行权限：所有用户
语法：last
功能描述：列出目前与过去登入系统的用户信息
```

1. `范例：# last`

## 命令名称：lastlog

```
命令所在路径：/usr/bin/lastlog
执行权限：所有用户
语法：lastlog
功能描述：检查某特定用户上次登录的时间
```

1. `范例：# lastlog`
2. `# lastlog -u 502`

```

```

## 命令名称：traceroute

```
命令所在路径：/bin/traceroute
执行权限：所有用户
语法：traceroute
功能描述：显示数据包到主机间的路径
```

1. `范例：# traceroute www.baidu.com`

## 命令名称：netstat

```
命令所在路径：/bin/netstat
执行权限：所有用户
语法：netstat [选项]
功能描述：显示网络相关信息
```

 **选项：** 
*-t ： TCP协议* 
*-u ： UDP协议* 
*-l ： 监听* 
*-r ： 路由* 
*-n ： 显示IP地址和端口号*

1. `范例：`
2. `# netstat -tlun 查看本机监听的端口`
3. `# netstat -an 查看本机所有的网络连接`
4. `# netstat -rn 查看本机路由表`

## 命令名称：setup

```
命令所在路径：/usr/bin/setup
执行权限：root
语法：setup
功能描述：配置网络
```

1. `范例：# setup`

## 命令名称：mount

```
命令位置：/bin/mount
执行权限：所有用户
命令语法：mount [-t 文件系统] 设备文件名 挂载点
```

1. `范例：# mount -t iso9660 /dev/sr0 /mnt/cdrom`

# 关机重启命令

## shutdown [选项] 时间

**选项：** 
*-c： 取消前一个关机命令* 
*-h： 关机* 
*-r： 重启*

# 其他关机命令

1. `[root@localhost ~]# halt`
2. `[root@localhost ~]# poweroff`
3. `[root@localhost ~]# init 0`

## 其他重启命令

1. `[root@localhost ~]# reboot`
2. `[root@localhost ~]# init 6`

## 系统运行级别

```
0   关机
1   单用户
2   不完全多用户，不含NFS服务
3   完全多用户
4   未分配
5   图形界面
6   重启
```

1. `[root@localhost ~]# cat /etc/inittab`
2. `#修改系统默认运行级别`
3. `id:3:initdefault:`
4. ``
5. `[root@localhost ~]# runlevel`
6. `#查询系统运行级别`

## 退出登录命令

1. `[root@localhost ~]# logout`
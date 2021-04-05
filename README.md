# Linux服务器系统管理基础

## 实验目的
通过自学systemd，掌握命令和实战，加深对服务器系统管理的理解。

## 实验环境
Virtual Box
cmd终端

## 实验内容
学习systemd入门教程：口令篇
http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html
systemd入门教程：实战篇并通过asciinema录制

### 实验具体内容
#### 口令篇
查看历史版本
[![asciicast](https://asciinema.org/a/404824.svg)](https://asciinema.org/a/404824)
第三节
[![asciicast](https://asciinema.org/a/404828.svg)](https://asciinema.org/a/404828)
第四节
[![asciicast](https://asciinema.org/a/404829.svg)](https://asciinema.org/a/404829)
第五节
[![asciicast](https://asciinema.org/a/404832.svg)](https://asciinema.org/a/404832)
第六节
[![asciicast](https://asciinema.org/a/404833.svg)](https://asciinema.org/a/404833)
第七节
[![asciicast](https://asciinema.org/a/404835.svg)](https://asciinema.org/a/404835)
#### 实战篇
第一、二、三节
[![asciicast](https://asciinema.org/a/404854.svg)](https://asciinema.org/a/404854)
[![asciicast](https://asciinema.org/a/404856.svg)](https://asciinema.org/a/404856)

## 实验问题
1.有些进程和软件没有安装，需要进行手动安装，或者我通过查看进程选择用其他进程来代替。


## 自查清单

#### 1.如何添加一个用户并使其具备sudo执行程序的权限？

第一步：切换到root下：su，并输入密码
第二步：输入  vi /etc/sudoers，加入一行即可（cuc  ALL=(ALL)    ALL）


#### 2.如何将一个用户添加到一个用户组？

确认是否存在这个用户组，如果没有需要创建用户组。
用`useradd -G {group-name} username`代码添加

#### 3.如何查看当前系统的分区表和文件系统详细信息？

a.通过lsblk命令查看分区表
lsblk命令列出系统的所有块设备及其逻辑分区。
b.使用fdisk命令获取分区列表
代表格式化磁盘或固定磁盘的fdisk命令主要用于创建或删除硬盘分区。
c.使用sfdisk命令查看分区
sfdisk命令主要用于操作Linux上的分区表。
d.使用parted命令获取硬盘分区
列出设备分区表的另一种方法是通过parted命令。
#### 4.如何实现开机自动挂载Virtualbox的共享目录分区？

用VirtualBox虚拟机的共享文件夹设置共享的本地文件,进入虚拟机Ubuntu系统，打开终端，用root用户操作。首先在虚拟机上创建一个共享目录，实现挂载。
`mount -t {{filesystem_type}} {{path/to/device_file}} {{path/to/target_directory}}`
在/etc/fstab 文件末添加一项
`sharing /mnt/share vboxsf defaults 0 0   (或者sharing /mnt/share vboxsf rw,gid=100,uid=1000,auto 0 0）`

#### 5.基于LVM（逻辑分卷管理）的分区如何实现动态扩容和缩减容量？

动态扩容：对新增加的磁盘进行分区、创建物理卷。利用vgextend命令将新的物理卷加入到卷组中，增加逻辑卷大小，再通过resize2fs来修改文件系统的大小。

缩减容量：类似动态扩容，减小逻辑卷大小。

#### 6.如何通过systemd设置实现在网络连通时运行一个指定脚本，在网络断开时运行另一个脚本？

Unit区块Condition...和Assert...字段摄制条件。

#### 7.如何通过systemd设置实现一个脚本在任何情况下被杀死之后会立即重新启动？实现杀不死？

Service区块Restart字段设置为always，RestartSec设置小一点。
# shell脚本编程基础

## 实验目的
  掌握基本的shell脚本编程语言语法

## 实验环境
* Ubuntu (Virtual Box)
* VScode

## 实验内容
### 任务一
用bash编写一个图片批处理脚本，实现以下功能：
- [x] 支持命令行参数方式使用不同功能
- [x] 支持对指定目录下所有支持格式的图片文件进行批处理
  - [x] 支持以下常见图片批处理功能的单独使用或组合使用
  - [x] 支持对jpeg格式图片进行图片质量压缩
  - [x] 支持对jpeg/png/svg格式图片在保持原始宽高比的前提下压缩分辨率
  - [x] 支持对图片批量添加自定义文本水印
  - [x] 支持批量重命名（统一添加文件名前缀或后缀，不影响原始文件扩展名）
  - [x] 支持将png/svg图片统一转换为jpg格式图片

相关图片在after和before文件夹下。
### 任务二
1.用bash编写一个文本批处理脚本，对以下附件分别进行批量处理完成相应的数据统计任务：

- [x] 统计不同年龄区间范围（20岁以下、[20-30]、30岁以上）的球员数量、百分比
- [x] 统计不同场上位置的球员数量、百分比
- [x] 名字最长的球员是谁？名字最短的球员是谁？
- [x] 年龄最大的球员是谁？年龄最小的球员是谁？

2.用bash编写一个文本批处理脚本，对以下附件分别进行批量处理完成相应的数据统计任务：

- [x] 统计访问来源主机TOP 100和分别对应出现的总次数
- [x] 统计访问来源主机TOP 100 IP和分别对应出现的总次数
- [x] 统计最频繁被访问的URL TOP 100
- [x] 统计不同响应状态码的出现次数和对应百分比
- [x] 分别统计不同4XX状态码对应的TOP 10 URL和对应出现的总次数
- [x] 给定URL输出TOP 100访问来源主机

### 实验具体内容

1.安装imagemagick。
`sudo apt-get update`

`sudo apt-get install imagemagick`
2.打开Vscode，利用ssh远程连接虚拟机，将数据复制到虚拟机，编写相关基本，打开终端，输入执行语句，编译脚本程序。
`bash task1.sh -h`

3.将脚本程序编译后得到的图片和相关文本数据下载到宿主机，整理写成实验报告。

## 实验问题以及解决方法
1.shell脚本语言语法，例如case，while具体用法示例
A：翻阅课件和利用搜索引擎查询相关知识。
2.VScode ssh远程连接总是提示登录无响应timed out
A:禁用防火墙，只开启22号端口。
`sudo ufw disable`
`sudo ufw allow 22/tcp 允许所有的外部IP访问本机的22/tcp (ssh)端口`

## 参考资料
1.https://blog.csdn.net/m0_37864814/article/details/82961927

2.https://github.com/CUCCS/linux-2020-cuc-ty/blob/chap0x04/chap0x04/chap0x04_report.md

3.https://github.com/CUCCS/linux-2020-LyuLumos/tree/ch0x04
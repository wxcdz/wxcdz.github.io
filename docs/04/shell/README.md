# shell

## 文件目录管理

### 访问目录

```bash
# 进入目录
cd /usr/local
# 查看当前目录
pwd 
# 回退到上一次目录
cd -

```

### 文件和目录列表



```bash
# 查看文件目录列表
ls 
# 列表区分文件和目录
ls -F
# 显示隐藏文件
ls -a
# 显示长列表
ls -l
# 递归查看目录
ls -F -R
```

### 过滤列表

```bash
# ?代表一个字符
# *代表零个或多个字符

ls -l my_scr?pt

ls -l my*

ls -l my_scr[ai]t

ls -l my_scr[a-i]t

# !将不需要的内容排除在外
ls -l f[!a]ll
```



## 文件处理

### 创建文件

```bash
touch test_file
```

### 复制文件

```bash
# cp 目标文件 目标文件夹
# -i 参数 如果目标文件已经存在会提醒
[root@int webapps]# cp -i root.war root.war2
cp: overwrite ‘root.war2’? 

# 递归复制
cp -R webapps/ web

# cp命令使用通配符
cp *script mod_script/
```



### 重命名文件

```bash
# mv命令 可以将文件和目录移动到另一个位置或重命名
# 重命名
mv fail file

# 移动文件
mv file /opt

# 移动文件并修改文件名
mv /opt/file.txt /opt/fail.txt
```



### 删除文件

```bash
# -i 参数询问是否真的删除文件
rm -i file_a
```



## 目录处理

### 创建目录

```bash
# mkdir 命令
mkdir new_dir

# 创建多个目录使用 -p 参数
mkdir -p test1/test2/test3
[root@int web]# ls -R test1/
test1/:
test2

test1/test2:
test3

test1/test2/test3:

```

### 删除目录

```bash
# rmdir 删除目录(rmdir命令只删除空目录)
rmdir test1

# rm -r选项使得命令可以向下进入目录，删除其中的文件然后再删除目录本身
rm -ri test1

# -rf参数谨慎使用
rm -rf test1

```

## 文件内容

### 查看文件l类型

```bash
file test
```

### 查看整个文件

```bash
# cat 命令
cat test1
# -n 参数 给所有的行加上行号
cat -n test1
# -b 参数 给有文本的行加上行号
cat -b test1
# more 命令
more test1
# less 命令
less test1
```

### 查看部分文件

```bash
# tail 命令查看文件的后十行
tail /var/log/error.log
# -n 参数查看指定行
tail -n 100 /var/log/error.log

# head 命令查看文件的前十行
head /var/log/error.log
# -n 参数查看指定行
head -n 5 test1


```

##  监测程序

### 探查进程

```bash
# ps -ef 命令查看进程
UID        PID  PPID  C STIME TTY          TIME CMD
UID: 启动这些进程的用户
PID: 进程的进程ID
PPID: 父进程的进程号
C: 进程声明周期中的CPU利用率
STIME: 进程启动的系统时间
TTY: 进程穹顶时的终端设备
TIME: 运行进程需要的累计CPU时间
CMD: 启动的程序名称
```

### 实时监测进程

```bash
# top 命令
PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND 

PID： 进程的ID
USER: 进程属组的优先级
PR: 进程的优先级
NI: 进程的谦让度值
VIRT: 进程占用的虚拟内存总量
RES: 进程占用的物理内存总量
SHR: 进程和其它进程共享的内存总量
S:进程状态 D可中断的休眠状态，R运行状态，S休眠状态，T跟踪或停止状态，Z僵化状态
%CPU: 进程使用的CPU时间比例
%MEM: 进程使用内存占用可用内存比例
TIME+: 自进程启动到目前为止的CPU时间总量
COMMAND: 进程所对应的命令行名称，启动的程序名
```

### 结束进程

```bash
# kill 命令
kill PID
# killall 命令(谨慎使用)
# 结束所有以http开头的进程
killall http*
```

## 监测磁盘空间



##  处理数据文件

### 排序数据



### 搜索数据

```bash
# grep 命令
[root@int web]# grep t file1
two 
three
eight
ten
# -v参数 反向搜索
[root@int web]# grep -v  t file1
one
four
five
six
seven
nine
# -n参数 显示所在的行号
[root@int web]# grep -n two file1
2:two 
# -c参数 多少行含有匹配的模式
[root@int web]# grep -c t file1
4
# -e 参数指定每个模式
[root@int web]# grep -e t -e f file1
two 
three
four
five
eight
ten
```



### 压缩数据

```bash
# gzip 用来压缩文件
gzip file1

# gunzip 用来解压文件
gunzip file1.gz
```



### 归档数据

```bash
tar -cvf test.tar 
```


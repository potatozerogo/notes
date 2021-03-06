Linux学习笔记

#Linux命令：  
##文件目录命令  
man //显示命令介绍内容  
命令 --help //显示命令介绍内容  
cd //切换当前路径  
cd ~ //回到用户home目录  
ls //显示当前目录中的文件  
ls -a //显示当前目录中所有文件  
ls -l //显示当前目录中所有文件的详细属性  
ls -lh //显示当前目录中所有文件的详细属性和文件具体大小  
pwd //打印当前路径  
mkdir //创建目录  
rmdir //删除空目录  
mv //移动或重命名，文件或目录  
touch //创建文件  
cat //打印文件中的内容  
cat -b 文件名 //打印文件中的内容和行号  
echo //打印文本  
echo 文本 >> 文件名 //将文本添加到文件内容最后  
echo 文本 > 文件名 //将文本替换文件内容  
wc //打印文件的行数、单词数、字符数  
wc -l //单独打印行数  
wc -w //单独答应单词数  
wc -c //单独打印字符数  
rm //删除文件、空目录  
rm -r //可删除非空目录  
ln //创建硬链接文件  
ln -l //创建软链接文件  
cp //复制文件、目录  
cp -r //复制整个目录和其中的内容  
tar //打包和解包文件  
find -name //查找文件，根据文件名  
grep //查找文件中的内容  
grep -n //文中的内容的行号  
which 文件名 //查找文件位置  
##用户组命令  
sudo //暂时获得root权限  
su //更换用户  
adduser //增加新用户  
deluser //删除用户  
usermod //改变用户的用户组  
passwd //改密码  
addgroup //增加新用户组  
delgroup //删除用户组  
##文件权限命令
chmod //修改文件读、写、执行的属性  
sudo chmod 666 文件名 //修改为可读可写  
sudo chmod 777 文件名 //修改为可读可写可执行  
chown //修改文件用户归属  
chgrp //修改文件用户组归属  
umask //显示文件权限掩码  
##磁盘管理命令
df -h //显示文件系统  
du -h //显示磁盘信息  
mount //挂在文件系统  
umout //解除挂在文件系统  
##网络命令
ping  
ifconfig //网络设置  
ifconfig //设备名称 ip地址 设置ip地址  
ifconfig //设备名称 down 关闭网卡  
ifconfig //设备名称 up 开启网卡  
##其他命令
clear //清屏幕  
reboot //重启  
poweroff //关机  
sudo sh -c '命令内容' //合并命令由于权限  
##进程命令
jobs //查看后台进程  
fg jobID号 //将进程切换至前台  
pstree //查看进程间关系  
ps -ef |more //查看进程明细，|more为分页显示 
ps aux |more //a:一个终端的所有进程；u:内存使用；x:没有关联的控制终端进程  
ps axjf //j:进程组pgid,会话sid,父进程ppid；f:以ASCii显示进程层次关系   
###PS命令显示的列表介绍   
user：进程是那个用户产生的  
pid：进程id  
%cpu：占用cpu的百分比  
%mem：占用内存的百分比  
vsz：进程使用虚拟内存大小  
rss：进程使用物理内存大小  
tty：进程关联的终端  
stat：进程的状态  
start：进程开始的时间   
time：进程运行的时间  
commmand： 进程执行的具体程序  
ppid：父进程id  
pgid：进程组id  
sid：进程所在对话的id  
tpgid：值为-1表示进程为守护进程  
uid：进程的用户id  
##技巧
命令或文件名自动补全 Tab键  
显示可能的文件名 两下Tab键  
重复上条命令   ！！  
Ctrl+z 暂停并切换至后台  

//————————————————  
#文件信息第一位表示文件类型：
##Linux文件类型：
使用 ls -l查看  
- 普通文件  
d 目录文件  
l 连接文件  
c 字符设备文件  
b 块设备文件  
套字节文件  
管道文件  

#文件信息第二位至第十位表示：  
用户权限（读、写、执行）、用户组权限（读、写、执行）、其他用户权限（读、写、执行）。  
r 读  
w 写  
x 执行  
- 无该权限  

//——————————————————  
#UID
root：0  
系统用户：1～999  
普通用户：1000+  

//———————————————————  
#VI编辑器
##编辑模式
i 在光标当前位置插入文本  
a 在光标的下一个位置插入文本  
o 在光标下一行插入新行  
r 替换当前光标单个字符  
R 替换当前光标后的字符，Esc退出  
Esc 推出编辑模式  

##阅读模式
行号 shift+g 跳转到该行号  
shift+g 跳转末尾行  
gg 跳转到第一行  
/查找的文本 查找文本  
n 查找下一个  
N 查找上一个  
u 撤销上一部操作  
dw 删除光标所在单词  
dd 删除当前行  
数量dd 删除当前行开始的n行  
x 剪切光标当前内容  
y 复制光标当前内容  
yy 复制当前行  
数量yy 复制当前行开始的n行  
p 粘贴在下一行  
P 粘贴在上一行  
v 区块选择  
V 行区块选择  

:w 保存文件  
:w 文件名 另存为  
:r 文件名 读入其他文件  
:q 退出  
:q！ 强制退出，不保存  
:wq 保存退出  
:set nu 显示行号  
:set nonu 不显示行号  
:! Linux命令 不退出VI，执行linux命令  

//——————————————————————————  
#shell脚本语法
##变量定义
variable=value  
variable='value value' //使用''中间可以有空格  
variable1="${variable} value" //使用""可以包含其他变量引用  

##使用变量
$variable  
${variable}  

##变量赋值
variable='command'  
variable=$(command)  

##删除变量
unset variable  

##特殊变量
$0        当前脚本的文件名。  
$n（n≥1） 传递给脚本或函数的参数。n 是一个数字，表示第几个参数。例如，第一个参数是 $1，第二个参数是 $2  
$#        传递给脚本或函数的参数个数  
$*        传递给脚本或函数的所有参数  
$@        传递给脚本或函数的所有参数。当被双引号`" "`包含时，$@ 与 $* 稍有不同  
$?        上个命令的退出状态或者获取函数返回值  
$$        当前 Shell 进程 ID。对于 Shell 脚本，就是这些脚本所在的进程 ID  

##变量操作
echo “$variable” //打印变量值  
variable=$aString //变量与字符串拼接，并排放  
read variable //从键盘读如数据  
read -p "input:" variable //有提示的读入数据  
var=$((a+b)) //对整数进行数学运算  
command1 && command2 //逻辑与 command1成立才会执行command2  
command1 || command2 //逻辑或 command1不成立才会执行command2  

检测某个条件是否成立  
test expression和[ expression ]  
| 选 项       | 作 用                                  |  
| ----------- | -------------------------------------- |  
| -eq         | 判断数值是否相等                       |  
| -ne         | 判断数值是否不相等                     |  
| -gt         | 判断数值是否大于                       |  
| -lt         | 判断数值是否小于                       |  
| -ge         | 判断数值是否大于等于                   |  
| -le         | 判断数值是否小于到等于                 |  
| -z  str     | 判断字符串 str 是否为空                |  
| -n  str     | 判断字符串str是否为非空                |  
| =和==       | 判断字符串str是否相等                  |  
| -d filename | 判断文件是否存在，并且是否为目录文件。 |  
| -f filename | 判断文件是否存在，井且是否为普通文件。 |  

管道
command1 | command2 //将第一个命令的结果，传递个第二个命令。  

//----------------------------------------------------------  
##deb安装包，安装软件
dpkg -i  xxxx.deb //安装软件  
dpkg -L xxxx //查看软件安装目录  
dpkg -r xxxx //卸载软件  
dpkg -b //构建deb安装包，构建deb安装包，同时需要使用野火提供的shell脚本，生成deb安装包所需要的其他文件信息。  

##apt
sudo apt update //更新软件列表信息  
sudo apt install xxxx //安装软件  
sudo apt install xxxx -y //默认安装软件  

//-----------------------------------------------------------------------  
#git
ssh-keygen -t rsa -C "youremail@example.com" //创建SSH KEY,然后贴到github上  
git clone 远程仓库地址 //克隆远程仓库  
git pull 远程仓库地址 //从远程仓库中更新  
git init //建立仓库  
git add 文件名 //添加文件给仓库  
git commit -m "注释" //提交文件给仓库  
git remote add origin 远程仓库地址 //添加远程仓库  
git push -u origin master //提交文件给远程仓库(第一次)  
git push origin master //提交文件给远程仓库  
git log //查看版本日志  

//-------------------------------------------------------------------------  
#共享文件
showmount -e //显示本地共享文件夹  
showmount -e 对方主机IP//显示对方共享文件夹  
sudo mount -t nfs 对方主机IP:对方共享文件夹路径 本地对应路径 //挂在共享文件夹  
//-------------------------------------------------------------------------  
#GCC
sudo apt install gcc -y //安装gcc  
sudo apt install gcc-arm-linux-gnueabihf -y //安装arm_gcc  
gcc 文件名.c -o 生成文件名称 -v//用gcc编译并连接生成可执行文件，-o制定编译后的文件名，-v显示编译过程  
sudo arm-linux-gnueabihf-gcc 文件名.c -o 生成文件名称 //交叉编译arm文件  
sudo gcc -E 文件名.c -o 预处理文件名.i //生成预处理文件  
sudo gcc -S 预处理文件名.i -o 汇编文件名.s //编译成汇编文件  
sudo gcc -c 汇编文件名.s -o 可重定位文件名.o  //编译成可重定位文件  
sudo gcc 可重定位文件名.o -o 可执行文件名 //连接成可执行文件，默认动态链接  
sudo gcc 可重定位文件名.o -o 可执行文件名 -static //连接成可执行文件，静态链接  
sudo gcc -I头文件目录 //编译添加头文件路径  

//------------------------------------------------------------------------  
#Makefile
sudo make -f Make文件名 //指定执行Make的文件  
.PHONY 目标名 //可以指定伪目标，每次都编译
##变量  
###系统变量  
$(CC) //一般指编译器  
$(AS) //一般指汇编器  
$(MAKE) //一般指Make工具  
###自定义变量  
= //延迟赋值，附变量最后的值  
:= //立即赋值  
?= //空赋值，只有当变量为空时赋值才有效  
+= //追加赋值，在原先的值后面加上新的值  
###自动化变量  
$< //第一个依赖文件  
$^ //全部的依赖文件  
$@ //目标  
##模式匹配  
% //匹配任意多个非空字符  
##默认规则  
.o文件默认使用.c文件来编译  
##条件分支
ifeq ($(variable),xxx) //ifeg后面有个空格  
	执行语句  
else  
	执行语句  
endif  
  
ifneq ($(variable),xxx) //ifeg后面有个空格  
	执行语句  
else  
	执行语句  
endif  
##函数
$(patsubst PATTERN,REPLACEMENT,TEXT) //模式替换  
$(patsubst %.c,%.o,x.c.c bar.c) 输出 x.c.o bar.o  

$(notdir NAMES...) //去除目录路径，只留文件名  
$(notdir src/foo.c hacks) 输出 foo.c hacks  

$(wildcard PATTERN) //找出匹配的文件名  
$(wildcard *.c) 输出 所有.c文件名  

$(foreach VAR,LIST,TEXT) //遍历  
dirs := a b c d  
files := $(foreach dir,$(dirs),$(wildcard $(dir)/*))  
输出 a b c d目录下的所有文件  

/------------------------------------------------------------------------  

#文件系统-系统IO函数
##int fd;//定义文件描述符  
文件描述符的值实际上是进程中file_struct.fd_array的下标，fd_array的结构体包含了文件的一些信息     
##fd = open("filename",flags,mode);//打开文件（文件名，打开模式，文件模式）
###flags://(flag_1|flag_2)多个flag用|连接
####主模式，三选一：
- O_RDONLY//只读  
- O_WRONLY//只写
- O_RDWR//读写  
####副模式，多选：
- O_CREAT//新建模式  
- O_APPEND//追加模式，在文件末尾开始  
- O_DIRECT//直接IO模式，不经过页缓存区，直接磁盘。 
- O_SYNC//同步模式，不需要sync() 就将页缓存区的内容写入磁盘  
- O_NO_BLOCK//非阻塞模式  

返回:文件描述符,错误返回-1 
###open()依赖的库
- #include<sys/types.h>   
- #include<sys/stat.h>  
- #include<fcntl.h>  

##off_t lseek(int fd,off_t offset,int whence);// 设置读写位置（文件描述符，偏移量，基准位置） 
###whence
- SEEK_SET //基准位置为文件开头  
- SEEK_CUR //基准位置为当前位置  
- SEEK_END //基准位置为未见末尾  

##size_t read(int fd,void *buff,size_t write_len);//读文件内容 （文件描述符，读buff，读长度） 
返回:读到的长度，错误返回-1  

##size_t write(int fd,void *buff,size_t read_len);//读文件内容（文件描述符，写buff，写长度）  
返回:写入的长度，错误:返回-1    

##sync();//强制把页缓存区的内容写入磁盘
页缓存区：一页=4KB  

##close(fd);//关闭文件（文件描述符）
错误返回-1    

###lseek()read()write()sync()close()依赖的库

- #include<unistd.h>  

#文件系统-标准IO函数
fopen()  
fclose()  
fread()  
fwrite()  
fseek()  
fflush() //强制把IO缓存区数据写入也缓存区  

##文件IO五大模式
- 阻塞模式  
- 非阻塞模式  
- IO多路复用  
- 异步IO  
- 信号驱动IO  

//----------------------------------------------------------------------------  
#进程
##pid_t fork(void)//创建子进程  
返回，老进程返回PID，新进程返回0，失败返回-1  
依赖的库 #include<unistd.h>  
##exec类子进程偷梁换柱
####int execl(const char *path,const char *arg,...,NULL)
//列表方式传递参数。execl("执行文件路径","参数1","参数2",...,NULL)  
  
####int execlp(const char *file,const char *arg,...,NULL)
//使用环境变量列表方式传递参数。execl("执行文件","参数1","参数2",...,NULL)  
  
####char *arg[] = {const char *arg,...,NULL}
//参数数组
####int execv(const char *path,*const arg[])
//数组传递参数。execv("执行文件路径",参数数组)   
  
####char *arg[] = {const char *arg,...,NULL}
//参数数组  
####char *envp[] = {const char *arg,...,NULL}
//自定义环境变量数组  
####int execv(const char *path,char *const arg[],*char const envp[])
//数组传递参数(用户提供自定义环境变量)。execv额("执行文件路径",参数数组，自定义环境变量数组) 

##进程退出
####void exit(int status);
//退出进程，io缓存去数据处理    
####void _exit(int status);
//直接退出

##wait()
####pid_t wait(*status)
//等待退出函数  
返回，成功子进程pid，失败-1  

####WIFEXITED(statue) 正常退出，值为1
####WEXITSTATUS(status) 获得子进程退出值  

//--------------------------------------------------------------------------
#信号
##无名管道用于父子进程（有情缘关系）间的通信
##有名管道
##查看信号类型命令
kill -l
##解决某个进程
kill PID
##解决某个停止状态的进程
kill -9 PID
##结束进程快捷键
Ctrl+c
Ctrl+\
##暂停进程快捷键
Ctrl+z

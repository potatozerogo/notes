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

##技巧
命令或文件名自动补全 Tab键  
显示可能的文件名 两下Tab键  
重复上条命令   ！！  

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

//-------------------------------------------------------------------------  
#共享文件
showmount -e //显示共享文件夹  
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
###模式匹配  
% //匹配任意多个非空字符  
###默认规则  
.o文件默认使用.c文件来编译  
###条件分支
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






## shell is kernel's shell

### bash shell

1. type 查看命令来源，内置 外置 别名等

### shell 的变量功能
1. 变量的可变性和方便性
2. 影响bash环境操作的变量,每个用户分配了bash的执行程序，系统通过PATH查找命令
3. 脚本程序设计的好帮手--变量

### 变量的显示与设置

1. echo ${变量}
2. unset 变量  
`在一般状态下，父进程的自定义变量是无法在子进程内使用的的，但是通过export将变量变成环境变量后，就能够在子进程下面使用了。`
3. $ 本shell的PID 
4. ? 上一个shell命令的回传码
5. export 自定义变量转成环境变量

### 语系变量 locale
1. locale -a
2. locale
3. cat /etc/default/locale  Ubuntu 中查看语系配置

### 变量键盘读取、数组与声明
1. read [-pt] variable  
 
``read -p "plz input " -t 30 testVar``  
2. declare [-aixr] variable

+ -a 将后面的变量定义为数组（array）类型
+ -i 将后面的变量定义为数字（integer）类型
+ -x 同export ,将后面的变量定义为环境变量
+ -r 将变量设置为 readonly 类型，该变量不能被更改内容，也不能重设
+ -p 列出变量的类型

````
测试： 
declare -i sum=1+1  // 定义为数字类型
declare -x sum      // 设置为环境变量
export | grep sum   // 查看环境变量是否设置成功
declare +x sum      // 取消环境变量设置
````

### 数组（array）变量类型

````
// 定义数组变量
var[1]="value1"
var[2]="value2"
var[3]="value3"
// 注意数组变量的读取
echo ${var[1]}
echo ${var[2]}
echo ${var[3]}
````

 













     
 







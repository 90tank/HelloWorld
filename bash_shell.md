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
[^注意]：在一般状态下，父进程的自定义变量是无法在子进程内使用的的，但是通过export将变量变成环境变量后，就能够在子进程下面使用了。


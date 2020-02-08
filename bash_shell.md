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

### ulimit 修改 shell 资源限制。
help ulimit 查看

### 变量内容的删除、替代、删除
|变量设置方式|说明|
|---|:---:|
|${var#keywords}|若变量内容从开始的数据符合关键字，则符合的最短数据删除|
|${var##keywords}|若变量内容从开始的数据符合关键字，则符合的最长数据删除|
|${var%keywords}|若变量内容从尾向前的数据符合关键字，则符合的最短数据删除|
|${var%keywords}|若变量内容从尾向前的数据符合关键字，则符合的最长数据删除|
|${var/oldkeywords/newkeywords}|用新的替换第一个旧的字符串|
|${var//oldkeywords/%keywords}|替换全部符合的|

### 变量的测试与替换
`username=${username-root} 如果username变量未设置，则将root给变量（username未未空字串，认为已设置）`

`username=${username:-root} 如果username为空或者未设置，都能够替换后面的内容 `
注意： - （减号并不会影响原始变量的值，若要改变，则使用= 等号）
`unset str;echo ${str?nova} 旧变量不存在情况下 判断不存在 可用 ?`
 

### 命令与别名设置
1. alias
如 alias cls='clear' 
2. history


### 数据流重定向
1. 标准输入（std）:代码为0，使用< 或者 << 
2. 标准输出（stdout）:代码为1，使用> 或者>>
3. 标准错误输出（stderr）:代码为2，使用 2> 或者 2>>

### /dev/null 垃圾桶黑洞设备
```shell
# 范例 
# 将stdout 和stderr分别存到不同的文件去
find /home -name .bashrc > list_right 2> list_error
# 将stdout 和stderr分别存到同一个文件去
find /home -name .bashrc > list 2>&1 
``` 

### 选取命令： cut 、grep

+ cut 可以将一段信息的某一段切出来  
`last | cut -d ' ' -f 1 从last输出的行中窃取以空格split后之后的第一个字段`

+ grep 

###排序命令

1. sort
2. uniq　[-ic]  -ｉ 表示去重、-ｃ 统计次数
```ｓhell
young@z:~ $ last | cut -d ' ' -f 1 |sort|uniq //去重了

reboot
wtmp
young

young@z:~ $ last | cut -d ' ' -f 1 |sort|uniq -c
      1 
      1 reboot
      1 wtmp
      1 young

```
3. wc [-lwm] 　行、单词、多少字符
　
### 双向重定向：ｔｅｅ 
+ tee要结合管道‘　| ’使用
```shell
# 将登录信息点到界面，并且重定向到文件中
young@z:~ $ last | tee last.list |cut -d ' ' -f1
young
reboot

wtmp
young@z:~ $ cat last.list 
young    :0           :0               Sun Feb  2 10:13   still logged in
reboot   system boot  5.3.0-28-generic Sun Feb  2 10:11   still running

wtmp begins Sat Feb  1 23:39:59 2020

```

### 切割命令
1. split 
split [-bl] file PREFIX
+ split　-b 300k file //按照３００ｋ大小进行切割
+ split -l 10 file  








     
 







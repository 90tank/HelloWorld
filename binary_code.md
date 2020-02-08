### **二进制编码**


**原码、反码、补码转换**

|类型  |表示形式|
|-----|-----|
|原码  |即数据的二进制表示形式(带符号位)|
|反码  |按位取反(符号位不变)|
|补码  |反码加一|


**正数与负数**
**正数原码反码补码相同 ，负数按照上表计算**  
  
|编码|举例：正数1|举例：负数1   |
|---|---------|------------|
|原码| 00000001|  1000 0001 |
|反码| 00000001|  1111 1110 |
|补码| 00000001|  1111 1111 |

### 应用场景
[见ArrayDeque数据结构分析](https://github.com/CarpenterLee/JCFInternals/blob/master/markdown/4-Stack%20and%20Queue.md)
```java
//addFirst(E e)
public void addFirst(E e) {
    if (e == null)//不允许放入null
        throw new NullPointerException();
    elements[head = (head - 1) & (elements.length - 1)] = e;//2.下标是否越界
    if (head == tail)//1.空间是否够用
        doubleCapacity();//扩容
}
```
以上是一段 _循环数组_ 操作:  
elements.length 的长度是2的指数倍
head = head-1 ,用于计算循环数组中head的位置：  
head-1（正数） & elements.length-1 结果为head-1本身，相当于索引往前移动一位；  
该操作也相当于 (head-1)%(elements.length-1) ，即取余;        
head-1（负数，只能是 -1）& elements.length-1,根据前面的编码，此处结果为elements.length-1

-1 的补码表编码为      ： 1111 1111  
 elements.length-1   : 0xxx xxxx  
 逻辑与的结果为 0xxx xxxx,即elements.length-1，达到数组结尾，紧接着就执行扩容DoubleCapacity()
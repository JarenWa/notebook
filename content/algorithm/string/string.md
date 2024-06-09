
算法学习-Java字符串处理及其常用API
https://blog.csdn.net/qq_44036439/article/details/126188967

String str = "xx";
str.length();

Char[] s;
s.length;


StringBuffer


## 问题1
### Java中的 String 是不可变的，意味着一旦创建，你就不能改变它的内容。

```
s.charAt(start) ^= s.charAt(end);
s.charAt(end) ^= s.charAt(start);
s.charAt(start) ^= s.charAt(end);
```
这段代码尝试直接修改字符串中的字符，但这在Java中是不被允许的，因为 String 对象是不可变的。即使 String 是可变的，charAt 方法返回的也是一个值，而不是引用，因此你无法用这种方式为字符串中的字符赋予新的值。

### 解决
这个问题的正确方法涉及从字符串创建一个 char 数组，对数组进行交换操作，然后从数组创建一个新的字符串。
```
char[] arr = s.toCharArray();
...
return new String(arr);
```

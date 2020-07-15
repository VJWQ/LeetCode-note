Java 的 String 是一个类（Class）  
C++ 的 string 是一个类  
Python 的str是一个类  

# String 题目中的常见问题

## 如何判断两个字符串相等  

### Java
- **Java中不能直接用 == 判等。使用a.equals(b)。**
  - 使用“==”判断的相等时指相同的内存地址，也就是同一个对象实例。 == 只有在内存一样的时候才返回true。
  - 使用equals方法判断的相等在不同的对象中实现不同，意义也不同：
    - 在String类中首先判断内存地址是否一致，如果一致返回true，否则比较字符串的内容是否一致，如果内容一致也返回true。
    - StringBuilder类并没有重写equals方法，因此使用equals比较时，需要是同一个实例才会返回true。否则返回false。

- 因此，使用String类的equals方法是比较内容是否一致，而使用“==”是比较实例是否是同一个实例。

#### Java创建字符串的过程
- 在使用“=”赋值时，如果内存中已经有这个字符串，就会直接将其地址给这个变量，不会产生新的字符串。
```java
// Output is yes
String sa = "abc";
String sb = "abc";
if (sa == sb) {
    System.out.println("Yes");
} else {
    System.out.println("No");
}
```
- 当使用“+”或者“concat”方法拼接字符串的时候，会创建一个新的字符串，占用新的内存空间，因此使用“==”判断时返回false。

### C++
- 直接使用==判断字符串是否相等。

### Python
- 直接使用==判断字符串是否相等。

## 取出第 i 个字符以及字符串的遍历  

### Java
- String 不支持下标索引的方式访问，所以需要使用charAt(i)的方式访问对应位置的字符。同时也就没有办法使用下标的方式对String进行修改。
```java
String s = new String("Hello");
for(int i = 0; i < s.length(); i++) {
    char c = s.charAt(i);
}
```
- String是一种不可变类，字符串一但生成就不能被改变。+/replace()等方法会产生新的字符串，不会更改原有字符串。


### C++
- c++中的字符串是可变的，可以直接用s[i]=x的方式改变字符串。
```cpp
string s = "Hello";
for (int i = 0; i < s.size(); ++i) {
    s[i] ...
}
// or: 
for (char c: s) {
    c...
}
// visit and replace: 
for (char& c: s) {
   c...
}
```

### Python
- str是一种不可变类，字符串一但生成就不能被改变。+/replace()等方法会产生新的字符串，不会更改原有字符串。

```python
s = "Hello"
for i in range(len(s)):
    s[i].....
# or:
for c in s:
    c......
```

## null 和 "" 
- null表示空对象
- ""表示空串

### Java
- Java中一切皆对象的思想，null用来表示空对象。不能对空对象做任何操作，除了"=" 和"=="。
```java
String s = null;
String s = "";
```

### C++
```cpp
string &p = *static_cast<string *>(nullptr);
string s;
```

### Python
```python
s = None

s = ""
s = str() # equals to s= ''
```
# 常见的字符串函数
## Java

```java
String demo = "Hello,world!";
1.int length = demo.length(); //获取字符串的长度
2.boolean equals = demo.equals("Hello,world"); // 比较两个字符串相等
3.boolean contains = demo.contains("word"); // 是否包含子串
4.String replace = demo.replace("Hello,", "Yeah@"); // 将指定字符串(或正则表达式)替换，返回替换后的结果
5.char little = demo.charAt(5); // 查找字符串中索引为5的字符（索引从0开始）
6.String trim = demo.trim(); // 将字符串左右空格去除，返回去除空格后的结果
7.String concat = demo.concat("Great!"); // 拼接字符串，返回拼接结果
8.char[] charArray = demo.toCharArray(); // 返回该字符串组成的字符数组
9.String upperCase = demo.toUpperCase(); // 返回该字符串的大写形式
10.String lowerCase = demo.toLowerCase(); // 返回该字符串的小写形式
```

## Python

```python
s = "Hello,World"
1.print(s[1]) # 'e', 取出某个位置的字符
2.print(s[1:6]) # 'ello,' ，字符串切片
3.print(len(s)) # 11, 返回字符串的长度
4.print("e" in s) # True, 返回字符是否在字符串中
5.print(s.lower()) # 'hello,world', 将字符串所有元素变为小写
6.print(s.upper()) # 'HELLO,WORLD', 将字符串所有元素变为大写
7.s += '...' # Hello,World... ，字符串拼接，在字符串后拼接另一个字符串
8.print(s.find('lo')) # 3, 返回第一次找到指定字符串的起始位置（从左往右找）
9.print(s.swapcase()) # hELLO,wORLD..., 将大小写互换
10.print(s.split(',')) # ['Hello', 'World...'], 将字符串根据目标字符分割
```



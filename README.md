> https://blog.csdn.net/CareChere/article/details/52315728?depth_1-utm_source=distribute.pc_relevant.none-task&utm_source=distribute.pc_relevant.none-task
> https://blog.csdn.net/qq_28633249/article/details/77686976
## 正则表达式的定义方法
1. 显示定义
> var 变量名 = new ReExp("正则表达式模式")
```javascript
var myRegex = new ReExp("[0-9]")
```
2. 隐式定义
> var 变量名 = /正则表达式模式/
```javascript
var myRegex = /[0-9]/
```
---
## test()方法
> test()方法返回的是个布尔值，符合，返回true，如果不符合，则返回false。
```javascript
    // 验证邮政编码: 6个字符都是字符串
    var str1 = '300929';
    var str2 = 'lupei'
    // 定义正则表达式
    var myregex = /\d{6}/;
    // 判断str1是否符合
    if (myregex.test(str1)) {
        document.write(str1 + '是正确的邮政编码' + '<br/>')
    } else {
        document.write(str1 + '不是正确的邮政编码' + '</br>')
    }
    // 判断str2是否符合
    if (myregex.test(str2)) {
        document.write(str2 + '是正确的邮政编码' + '<br/>')
    } else {
        document.write(str2 + '不是正确的邮政编码' + '</br>')
    }

// result:
// 300929是正确的邮政编码
// lupei不是正确的邮政编码
```
## 常用元字符
在正则表达式中，包括2种字符：
1. 普通字符；
2. 特殊字符(元字符);

普通字符就是a~z、0~9这类常见的字符。其中特殊字符又称为“元字符”。元字符之所以叫特殊字符，就是它的特点跟普通字符不一样。例如邮政编码中，我们限定只能输入6个数字，那“数字”这个概念怎么理解呢？这个时候我们就用到了元字符\d来代替。

#### 正则表达式元字符

| 元字符        | 说明   |
| --------   | -----:  |
| \d      | 匹配数字，相当于[0-9]   | 
| \D        |   匹配非数字，相当于[^0-9]   | 
| \w        |    匹配字母或数字或汉字或下划线    | 
| \W        |    匹配任意不是字母、数字、汉字或下划线的字符    | 
| \s        |    匹配任意的空白符，如空格、换行符、制表符等    | 
| \S       |    匹配任意不是空白符的字符    | 
| .（点号）        |    匹配除了换行符以外的任意字符    | 
| [...]        |    匹配方括号中的所有字符    | 
| [^...]        |    匹配非方括号中的所有字符    | 

举例: `0\d{2}-\d{8}`

以0开头，然后是两个数字，然后是一个连字号“-”，最后是8个数字。\d{2}表示数字重复2次，\d{8}表示数字重复8次。记住，\d匹配是“数字”，很常用。{2}、{8}这些是限定符的内容.
```JavaScript
    var str3 = '0579-12345678'
    var myPhone = /0\d{3}-\d{8}/
    if (myPhone.test(str3)) {
        document.write(str3 + '是中国的电话号码')
    } else {
        document.write(str3 + '不是中国的电话号码')
    }
    // resul: 0579-12345678是中国的电话号码
```
## 连接符
我们知道要想匹配数字，正则表达式就要这样写：
```javascript
var reg = /[0123456789]/
// 等价于
var reg = /[0-9]/
```
其中[]表示匹配方括号内的任一字符。在正则表达式中，匹配数字或者英文字母的书写非常不方便。因此，正则表达式引入了连接符“-”来定义字符的范围。
#### 正则表达式连接符
| 连接符        | 说明   |
| --------   | -----:  |
| [0-9]      | 匹配数字，等价于\d   | 
| [a-z]        |   匹配英文小写字母   | 
| [A-Z]       |    匹配英文大写字母   | 
| [0-9a-zA-Z]        |    匹配数字或英文字母    | 
```javascript
    var str4 = 'ksiee12'
    var myreg = /[0-9][A-Z]/
    if (myreg.test(str4)) {
        document.write(str4 + '匹配' + '</br>')
    } else {
        document.write(str4 + '不匹配' + '</br>')
    }
    // resul: 不匹配

```
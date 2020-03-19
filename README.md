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

普通字符就是a&sim;z、0&sim;9这类常见的字符。其中特殊字符又称为“元字符”。元字符之所以叫特殊字符，就是它的特点跟普通字符不一样。例如邮政编码中，我们限定只能输入6个数字，那“数字”这个概念怎么理解呢？这个时候我们就用到了元字符\d来代替。

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
    // result: 0579-12345678是中国的电话号码
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
    // result: 匹配

```
## 限定符
限定符，就是限定某个或某类字符出现的次数。例如，邮政编码都是6位数，匹配邮政编码的正则表达式是“\d{6}”，其中“{6}”就是限定符。
#### 正则表达式限定符
| 连接符        | 说明   |
| --------   | -----:  |
| +      | 重复1次或更多次   | 
| *       |   重复0次或更多次（任意次数）   | 
| ?      |    重复0次或1次（最多1次）   | 
| {n}       |    重复n次   | 
| {n,}       |    重复n次或更多次（最少n次）   | 
| {n,m}      |    {n,m}   | 
```javascript
    var str5 = 'ygoods'
    var myreg5 = /go+/
    // 匹配字母o必须出现1次或者更多次
    // 所以匹配上面正则表达式的字符串有go、good、god等，但是get、g就不匹配了。
    if (myreg5.test(str5)) {
        document.write(str5 + '匹配' + '</br>')
    } else {
        document.write(str5 + '不匹配' + '</br>')
    }
    // result: 匹配
```
## 定位符
定位符，就是限定某些字符出现的位置
#### 正则表达式定位符
| 连接符        | 说明   |
| --------   | -----:  |
| ^      | 限定开始位置的字符   | 
| $       |   限定结尾位置的字符   | 
| \b      |    限定单词（字）边界的字符  | 
| \B       |    限定非单词（字）边界的字符  | 
***注意：***

上尖号的使用有2种情况：（1）定位符；（2）[^…]元字符。

很多初学者容易混淆上尖号，其实大家可以这样理解：上尖号，只有一种特殊情况，就是[^…]这种元字符的时候，上尖号才表示“非”，其他情况，上尖号都是表示定位符。

“er\b”匹配“order to”中的er，但不匹配“verb”中的“er”。

“er\B”匹配“verb”中的“er”，但不匹配“order”中的“er”。

\B用得比较少，而\b用得更多一些，因为往往都是\b来匹配一个单词什么，也很好用。
## 转义字符
正则表达式包括2种字符：（1）普通字符；（2）特殊字符。如果我们要匹配正则表达式中的特殊字符，我们就必须在该特殊字符前面加上反斜杠“\”将其进行转义。

需要转义的字符有：$、(、)、*、+、.、[、]、?、\、/、^、{、}、|。这些字符都不需要记忆，见得多就自然而然记住了。
```JavaScript
var myregex = new RegExp("\\d{6}");
var myregex = /\d{6}/
```
对于上面正则表达式的定义，很多初学者会有疑问，为什么是“\\d{6}”而不是“\d{6}”？其实使用new关键字定义正则表达式，RegExp对象是一个字符串，因此这里必须使用JavaScript的转义字符（不同于正则表达式转义字符）。
## 分组符
分组又称为子表达式，即把一个正则表达式的全部或部分分成一个或多个组。其中，分组使用的字符为“(”和“)”，即左圆括号和右圆括号。分组之后，用小括号括起来的表达式看出一个整体来处理。
***举例***
```JavaScript
/(abc){2}/
/[abc]{2}/
/(a[h-n]){2}/
```
1. 第一个正则表达式：

① 使用()把abc分为一组；
② {2}表示把(abc)这一组重复2次；
因此，这个正则表达式匹配的是必须包含abcabc的字符串。

2. 第二个正则表达式：

① [abc]表示匹配a、b、c中任意一个字符；
② {2}表示把[abc]重复2次；
因此，这个正则表达式匹配的字符是ab、dac、cfbchj等中含有a、b、c中任意两个字符组合（比如ab、bc、ac）的字符串。

3. 第三个正则表达式：

① [h-n]表示匹配字母h~n中任意字母；
② 使用小括号()把a[h-n]分成一组；
③ 然后使用限定符{2}使得该组必须重复2次
因此，正则表达式匹配的字符有：aiai、ajaj123这一类。
## 选择符
选择符，很简单。在正则表达式中，选择符是“|”，用于选择匹配2个选项之中的任意一个，类似JavaScript中的“或”运算。

例如，“abc|def1”匹配的是“abc”或“def1”，而不是“abc1”或“def1”。如果要匹配“abc1”或“def1”，应该使用分组符，即“(abcd|efgh)1”。
## 优先级顺序
运算符是有一定的优先级顺序的，例如*就比+先运算。在正则表达式中，同样存在优先级顺序。正则表达式存在元字符、限定符、转义字符、|等运算符。在匹配过程中，正则表达式都是先规定了这些运算或表达式的优先级。
| 运算符或表达式        | 说明   |
| --------   | -----:  |
| \     | 转义符   | 
| ()、(?:)、(?=)、[]       |   圆括号或方括号   | 
| *、+、?、{n}、{n,}、{n,m}     |    限定符  | 
| ^、$、\b、\B       |    位置和顺序  | 
| |      |    选择符，“或”运算  | 
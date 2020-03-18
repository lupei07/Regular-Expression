## 正则表达式的定义方法
1. 显示定义
> var 变量名 = new ReExp("正则表达式模式")
```
var myRegex = new ReExp("[0-9]")
```
2. 隐式定义
> var 变量名 = /正则表达式模式/
```
var myRegex = /[0-9]/
```
---
## test()方法
```
<script>
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

</script>
// result:
// 300929是正确的邮政编码
// lupei不是正确的邮政编码
```
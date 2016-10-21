## 因为看代码不太容易，复习一下基础
1. Javascript里区分大小写
2. ‘；’分号在代码分行时可加可不加，为了避免出错，我还是要加上的。
3. 支持进制
 2进制，16进制，8进制
```
    1000=8
    0xff=15*16+15
    0377=3*8^2+7*8+7
```
4. 二进制浮点数和四舍五入的误差


```
var x=.3-.2;//30美分-20美分
var y=.2-.1;//20美分减去10美分
x==y//false
x==.1//false:.3-.2不等于.1
y==.1//true ：.2-.1等于.1
```
在javascript的真实运行环境中，0.3-0.2=0.099 999 999 999 999 98

并不是只在javascript中才出现，在任何使用二进制浮点数的编程语言中都会有这个问题。
所以进行金融计算的时候，要使用整数的美分，而不是小数的美元

5.字符串

```
s="hello world";
s[0]     //=>h
s[s.length-1]//=>d
```

显示类型转换
toString()
```
String(false)//=>"false"或者使用false.toString()或者 x+""
除了null或undefined都可以使用字符串转换

Boolean(x)//!!x 

Object(x)//+x  new number(x)


```
valueOf() 如果存在任意原始值，它就默认将对象转换为表示它的原始值。

```
var d=new Date(2010,0,1)//2010年1月1日
d.valueOf(); //显示1970年1月1日以来的毫秒数
```

```
var now=new Date();
typeof(now+1);//=>"string":"+"将日期转换为字符串
typeof(now-1);//=>"number":"-"将日期转换为数字
now==now.toString()//=>true:隐式和显示的字符串转换
now>(now-1);//=>true:">"将日期转换为数字
```
- [ ] 函数作用域和声明提前

```
var scope="global";
function f(){
    console.log(scope);//输出“undefined”,而不是"global"
    var scope="local";
    console.log(scope);//输出"local"
}
在函数体内局部变量掩盖了同名全局变量，而在函数体内，由于函数作用域的特性，局部变量在整个函数体内始终是有定义的。但是，只有在函数执行到var语句的时候，局部变量才会被真正的赋值。
```
相当于下面的代码
```
function f(){
    var scope;
    console.log(scope);//输出“undefined”
    scope="local";
    console.log(scope);//输出“local”
}
```
var 定义的变量不能被delete删除
```
var i=1;
    j=1;
this.k=1;
delete i;//false变量并没有被删除
delete j ;//true变量被删除
delete k;//true 变量被删除
```





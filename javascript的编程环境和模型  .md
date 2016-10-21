## javascript 声明和初始化变量
- [ ] 变量的声明
```
var number;
var rate=1.2;
var greeting="hello,world";
var flag=false;
```
## javascript中的算术运算和数学库函数
>
- [ ] 算术符号，运算，和数学表达式

```
var x=3;
var y=1.1;
print(x+y);
print(x*y);
print((x-y)*(x+y));
var z=9;
print(Math.sqrt(z));
print(Math.abs(y/x));
```
> 输出结果
- 4.1
- 3.3000000000000003   //为什么最后有个3
- 7.7899999999999999   //为什么不是7.79
- 3
- 0.3666666666666667   //为什么不是0.366666667
- [ ] 计算结果精度

```
var x=3;
var y=1.1;
var z=x*y;
print(z.toFixed(2));     
```
显示结果 3.30    //小数点后2位
## 判断结构
- [ ] if-else if-else
- 
```
var mid=25;
var high=50;
var low=1;
var current=13;
var found=-1;
if(current<mid){
    mid=(current-low)/2;
}
else if(current>mid){
    mid=(current+high)/2;
}
else{
    found=current;
}
```
- [ ] switch 语句
-
```
putstr("Enter a month number:");// putstr是什么
var monthNum=readline();//readline是什么
var monthName;
switch(monthNum){
    case"1":
        monthName="january";
        break;
    case"2":
        monthName="february";
         break;
    case"3":
        monthName="march";
         break;
    case"4":
        monthName="april";
         break;
    case"5":
        monthName="may";
         break;
    case"6":
        monthName="june";
         break;
    case"7":
        monthName="july"
         break;

     case"8":
        monthName="august";
         break;
    case"9":
        monthName="september";
         break;
    case"10":
        monthName="october";
         break;
    case"11":
        monthName="november";
         break;
    case"12":
         monthName=""december;
          break;
    defult:
    print("bad input");
}
```
## 循环结构
- [ ] while循环
```
var number=1;
var sum=0;
while(number<11){
    sum+=number;//sum=number+sum
    ++number;//number=number+1
}
print(sum);//显示 55
```

sum | number
---|---
1 | 1
3 |2
6|3
10|4
15 | 5
21|6
28|7
36|8
45|9
55|10
- [ ] for 循环求和
- 
```
var number=1;
var sum=0;
for(;number<11;number++){
    sum+=number;
}
print(sum);//显示144
```
==问题：number++ 和 ++number有什么区别==

在循环里面没有区别

本身的表达式区别

```
i++  ：先引用后增加
++i  ：先增加后引用
i++  ：先在i所在的表达式中使用i的当前值，后让i加1

++i  ：让i先加1，然后在i所在的表达式中使用i的新值
```

##     函数
- [ ] 对象和面向对象编程


> 银行账户checking和测试代码

```
function checking(amount){
    this.balance=amount;
    this.deposit=deposit;
    this.withdraw=withdraw;
    this.toString=toString;
}
function deposit(amount){
    this.balance+=amount;
}
function withdraw(amount){
    if(amount<=this.balance){
        this.balance-=amount;//this.balance=this.balance-amount;
    }
    else if{
        print("insufficient funds");
    }
}
function toString(){
    return"balance:"+this.balance;
}
//测试代码
var amount=new checking(500);
account.deposit(1000);
print(account toString());//1500
account.withdraw(750);
print(account toString());//750 
account.withdraw(800);//insufficient founds
print(account toString());//750

```
 account 是checking的构造函数，相当于克隆一个。


## this
- [ ] 作为对象的方法调用，this指向该对象
- 
```
var obj(){
    a:1; //键值对
    getA:function(){
        alert(this===obj);//输出：true
        alert(this.a);输出：1
    }
    
}
this.getA;
```
- [ ] 作为普通函数被调用时，this指向全局变量。在浏览器的javascript里，这个全局对象是window对象
- 
```
<html>
<body>
<div id="div1">我是一个div</div>

<script>
window.id='window';
document.getElementById('div1').onclick=function(){
    alert(this.id);//输出div1
    var callback=function(){
        alert(this.id);//输出window
    }
    callback();
}
</script>
</body>
```
- 用一个变量保存div节点的this

```
document.getElementById('div1').onclick=function(){
    alert(this.div);//输出div1
    var that=this;//保存div的引用
    var callback=function(){
        alert(this.id);//输出window
    }
```
- [ ] 函数构造器的返回。
- new 克隆一个构造器后，这个新的构造器返回的对象就是原函数中this指向的这个对象
- 
```
var myclass=function(){
this.name='seve';
};
var obj=new myclass();
alert(obj.name);//输出seve
```
- 当函数构造器显示的返回一个object类型的对象，那么就会返回这个对象，而不是前面代码中的this、

```
var myclass=function(){
this.name='seve';
return{   //显示的返回一个对象
    name='anne';
    //显示的返回一个对象       不是显示  为 return 'anne'
}
};
var obj=new myclass();
alert(obj.name);//输出anne
```

- 函数构造器调用和普通函数调用的区别

```
var obj={
    myname='seve';
    getname=function(){
        return this.myname;
    }
}

console.log(obj.getname());//输出 seve
- 当调用obj.getname()时，getname是作为obj对象的属性被调用的，
与前面函数构造器的调用一样，此时的this指向的是obj对象。
前面的构造器是new构造了一个克隆obj的函数，
其实相当于就是obj函数。所以两者没有差别

var getname2=obj.getname;
console.log(getname2());//输出 undefined
- 利用getname2变量替换obj.getname，并且调用getname2。此时的getname2函数就不是对象的属性，而是普通函数的调用方法，
所以this指向的是window，所以执行的结果是undefined.

若是 
var getname2=obj.getname();//相当于已经调用了函数构造器
console.log(getname2());//输出 save
```
## call AND apply
- [ ] 认识
- apply
funfction.(prototype.)apply(参数1 指定了函数体内this对象的指向，参数2 集合可为数组中的参数传递给被调用的函数)

```
var func=function(a,b,c){
    alert([a,b,c]);
}
func.apply(null,[1,2,3]);
```
-call

function,(prototype.)call（）；根apply一样，不同的是参数2不是数组，是一个个得数字
```
var func=function(a,b,c){
    alert([a,b,c]);
}
func.call(null,1,2,3);
```
- [ ] null是什么，有什么用
- 传入参数1为null,函数体内的this会指向默认的宿主对象，在浏览器中是window。
- 
```
var func=function(a,b,c){
    alert(this===window)//true
}
func.apply(null,[1,2,3]);
```
- 如果在严格模式下，函数体内的this还是为null
- 
```
var func=function(a,b,c){
“use strict”;
    alert(this===window)//false
    alert(this===null)
}
func.apply(null,[1,2,3]);
```
- 有时候使用call或者apply的目的不在于指向this指向，其他的，比如借用其他对象的方法，那么可以用null来代替某个具体的对象
- 
```
math.max.apply(null,[1,2,3,4,5])//输出5
```


- [ ] 改变this的指向
- 

```
var obj1={
    name:'seve'
};
var obj2={
    name:'anne'
};
window.name='window';

var getname=function(){
    alert(this.name);
};

getname()
```

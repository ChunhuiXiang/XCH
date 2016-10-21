## 面向对象的javascript
- [ ] 面向对象的概念
- 在javascript中没有类的概念。
- 
```
function Person(name){
    this.name=name;
};
Person.prototype.getName=function(){
    return this.name;
};
var a=new Person('seve')
console.log(a.name);
console.log(a.getName());
console.log(Object.getPrototypeOf(a)=Person.prototype);//输出：true
```
1. 这里的person不是类，是函数构造器。用new 运算符调用，该函数是函数构造器。另一种是普通函数调用。
2. 用prototype向对象中添加新属性的方法。
3. getprototypeof,探索对象的原型
```
var proto = {};
var obj = Object.create(proto);
Object.getPrototypeOf(obj) === proto; // true
```
4._proto_属性默认指向它构造器的原型。
- [ ] 如果对象无法响应某个请求，会把请求委托向上递推，直到根对象
- 
```
var obj={name:'save'};

var A=function(){};
A.prototype=obj;

var a=new A();
console.log(a.name);
```
执行该段代码时，引擎做了下面几件事
1. 首先，尝试遍历a中的所有属性，没有找到name属性
2. 查找name属性这个请求被委托给对象a的构造器原型A,A被_proto_记录着并且指向A.prototype,而A.prototype
被设置为对象Obj.
3.在对象obj里面有name属性，并返回它的值。

```
graph LR
a-->A
```

```
graph LR
A-->obj
```


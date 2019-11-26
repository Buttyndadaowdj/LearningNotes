# TypeScript的简介
## JavaScript的超集
TypeScript是JavaScript类型的超集，它可以编译成纯JavaScript。TypeScript可以在任何浏览器、任何计算机和任何操作系统上运行，并且是开源的。
# 上手TypeScript
## 安装TypeScript
两种主要方式获取TypeScript工具：  

* 通过npm（Node.js包管理器）
* 安装Visual Studio的TypeScript插件
针对使用npm的用户：

	```ts
	npm install -g typescript
	```  
# TypeScript的基础类型
* 布尔类型（boolean）
* 数字类型（number）
* 字符串类型（string）
* 数组类型（array）
* 元祖类型（tuple）
* 枚举类型（enum）
* 任意类型（any）
* null和undefined
* void类型
* never类型
***
**typescript中为了使编写的代码更加规范，更有利于维护，增加了类型校验**  
**写ts代码必须指定类型**  
例如：  
```ts
var flag:boolean=true;  
flag=123;//错误写法 
 flag=false;//正确写法
 ```
## 布尔值
最基本的数据类型就是true/false值，在JavaScript和TypeScript里叫做boolean  
```ts
let isDone:boolean=false;
```
## 数字
```ts
let num:number=123;
```
## 字符串类型
```ts
let str:string='this is ts';
```
## 数组类型
ts中定义数组有两种方式：  
1. 第一种定义数组的方式  
	```ts
	var arr:number[]=[11,22]//表示数组里面必须是数字类型
	```
2. 第二种定义数组的方式  
	```ts
	var arr:Array<number>=[11,22,33]
	```
## 元组类型
**属于数组的一种**  
```ts
let arr:[number,string]=[123,'this is ts']//可以指定数组中每个的类型
```
## 枚举类型
随着计算机的普及，程序不仅只用于数值计算，还更广泛的用于处理非数值的数据。如果能在程序中用自然语言中相应含义的单词来代表某一状态，则程序就很容易阅读和理解。  
```ts
enum Flag{success=1,error=2}; 
let s:Flag=Flag.success;
console.log(s)//1
```
***
如果标识符没有赋值，那它的值就是下标  
```ts
enum Color{blue,red,'orange'}  
var c:Coloe=Color.red;  
console.log(c)//1
```  
```ts
enum Color{blue,red=3,'orange'}  
var c:Coloe=Color.red;  
console.log(c);//3  
var o:Color=Color.orange;  
console.log(o);//4
```  
## 任意类型  
**和es5里没有指定类型一样**  
```ts
var num:any=122;  
num='str'
```
## null和undefined
**其他（never类型）数据类型的子类型**  
```ts
var num:number;
console.log(num) //输出：undefined  报错  
var num:undefined;
console.log(num) //输出：undefined  正确
```  
## void类型
表示没有类型，一般用于定义方法的时候方法没有返回值  
```ts
function run():void{   
console.log('run')    
}
```
## never类型
是其他类型（包括null和undefined）的子类型，代表从来不会出现的值。  
这意味着声明never的变量只能被never类型所赋值  
```ts
var a:null;    
a=null    
var b:undefined    
b=undefined    
var c:never;  
c=123;//错误的写法  
c=(()=>{throw new Error('错误')})()
```
## Object
object表示非原始类型，也就是除了number、string、boolean、symbol、null或undefined以外的类型。使用object类型，就可以更好的表示像object.create这样的API.  
```ts
declare function create(o:object | null):void  
create({prop:0}) //ok 
create(null)  //ok  
create(42)//error
```
# 函数
1. 函数声明法    
	```ts
	function run():string{ return 'run'}
	```  
2. 匿名函数法    
	```ts
	var fun2=function():number{ return 123; } 
	```  
* 定义方法传参  
	```ts
	function getInfo(name:string,age:number):string{ return `${name}---${age}` }  
	getInfo('zhangsan',20)
	```
* 方法可选参数  
	**可选参数必须配置到参数的最后面**  
	```ts
	function getInfo(name:string,age?:number):string{if(age){return `${name}---${age}`}else{return `${name}---年龄保密`} }  
	getInfo('zhangsan',20)
	```
* 默认参数  
	```ts
	function getInfo(name:string,age:number=20):string{ return `${name}---${age}` }  
	`getInfo('zhangsan')
	```
* 剩余参数  
	```ts
	function sum(a:number,b:number,c:number,d:number):number{return a+b+c+d};   
	alert(sum(1,2,3,4))
	```    
**三点运算符  接收形参传递过来的值**  
	```ts
	function sum(...result:number[]):number{var sum=0;for(var i=0;i<result.length;i++){sum+=result[i]} return sum}; 
	alert(sum(1,2,3,4))
	``` 
* ts中的函数重载  
	```ts
	function getInfo(name:string):string;
	function getInfo(age:number):number; 
    function getInfo(str:any):any{
		if(typeof==='string'){
			return '我叫'+str}else{return '我的年龄是'+str
			}
		};
	```   
* 箭头函数  
	```ts
	setTimeout(()=>{alert('run')},1000)
	```
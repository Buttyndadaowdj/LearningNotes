# 类
##  类的定义
```ts
class Person{
    name:string; //属性   前面省略了public关键词
    construtor(n:string){//构造函数  实例化的时候触发的方法
        this.name=n;
    }
    run():void{  //方法
        alert(this.name);
    }
}
var p=new Person('张三')//实例化
p.run()
```
## 继承
```ts
    class Person{
    name:string; 
    construtor(n:string){
        this.name=n;
    }
    run():void{  
        alert(this.name);
    }
}
class Web wxtends Person{
    construtor(n:string){//继承父类需要写构造函数
        super(name);//初始化父类的构造函数
    }
}
var w=new Web('李四')
alert.(w.run());
```
### 继承的探讨--父类的方法和子类的方法一致
```ts
    class Person{
    name:string; 
    construtor(n:string){
        this.name=n;
    }
    run():void{  
        alert(this.name);
    }
}
class Web wxtends Person{
    construtor(n:string){//继承父类需要写构造函数
        super(name);//初始化父类的构造函数
    }
    //当子类和父类方法一样时，先在子类中寻找，没有找到才去父类中寻找
    run():string{
        return `${this.name}在运动-子类`
    }
    //子类在继承父类方法时，同时可以扩展自己的方法
    work(){
        alert(`${this.name}在运动`)//这是获取父类的属性
    }
}
var w=new Web('李四')
//alert.(w.run());
w.work();
```
## 类里面的修饰符
TypeScript里面定义属性的时候给我们提供了三种修饰符。**属性如果不加修饰符，默认是public（公有）**
### public
public:公有，在类里面、子类、类外面都可以访问  
**外部类访问公有属性**
```ts
    class Person{
        public name:string;
        constructor(name:string){
            this.name=name;
        }
    }
    var p=new Person('hhhh')
    alert(p.name)
```
### protected
protected:保护类型，在类里面、子类里面可以访问，在类外部没法访问  
```ts
    class Person{
        protected name:string;
        constructor(name:string){
            this.name=name;
        }
        run():void{  
            alert(this.name);
        }
    }
    class Web extends Person{
        constructor(name:string){
            super(name)
        }
        work(){
            alert(`${this.name}在工作`)
        }
    }
    var w=new Web('hhhh111')
    w.work();
    w.run()
    var p=new Person('哈哈哈哈')
    alert(p.name);//会报错，错误的写法，这是在外部调用属性
```
### private
private:私有，在类里面可以访问，子类、类外部都没法访问  
```ts
    class Person{
        private name:string;
        constructor(name:string){
            this.name=name;
        }
        run():void{  
            alert(this.name);
        }
    }
    class Web extends Person{
        constructor(name:string){
            super(name)
        }
        work(){
            console.log(`${this.name}在工作`)//会报错
        }
    }
    var p=new Person('哈哈哈哈')
    alert(p.run());//会执行，在当前类的方法里面会执行
```
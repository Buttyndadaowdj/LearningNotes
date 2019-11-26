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
}
var w=new Web('李四')
alert.(w.run());
```
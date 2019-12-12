# 组件
组件允许将UI拆分为独立可复用的代码片段，并对每个片段进行独立构思。  
## 函数组件与class组件  
**函数组件的编写**  
该函数是一个有效的React组件，接收唯一带有数据的“props”对象并返回一个React元素。  
```ts
    function Welcome(props){
        return <h1>Hello，{props.name}</h1>
    }
```
**ES6的class定义组件的编写**  
```ts
    class Welcome extends React.Component{
        render(){
            return <h1>Hello,{this.props.name}</h1>
        }
    }
```
***上述两个组件在React里是等效的***
## 渲染组件
*这段代码会在页面上渲染"Hello Sara"*
```ts
    function Welcome(props){
        return <h1>Hello，{props.name}</h1>
    }
    const element =<Welcome name="Sara"/>
    ReactDOM.render(
        element,
        document.getElementById('root')
    )
```
**这个例子中发生的步骤如下：**
1. 调用```ReactDOM.render()```函数，并传入```<Welcome name="Sara"/>```作为参数。
2. React调用Welcome组件，并将```{name:"Sara"}```作为props传入。
3. Welcome组件将```<h1>Hello,Sara</h1>```元素作为返回值。
4. React DOM 将DOM高效地更新为```<h1>Hello，Sara</h1>```
## Props的只读性
组件无论是使用函数声明还是通过class声明，都决不能修改自身的props。
**纯函数**  
纯函数是指该函数不会尝试更改入参，且多次调用下相同的入参始终返回相同的结果。
```ts
    function sum(a,b){
        return a+b;
    }
```
**非纯函数**
非纯函数就是函数自身更改了自己的入参
```ts
    function withdraw(account,amount){
        account.total-=amount
    }
```

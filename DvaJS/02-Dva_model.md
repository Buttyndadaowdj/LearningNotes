# Dva API 
网址：```https://dvajs.com/api/```
## model
model是dva中最重要的概念。  
model包含5个属性：  
1. namespace
namespace是model的命名空间，同时也是在全局```state```上的属性，只能用字符串，不支持```.```的方式创建多层命名空间。  
```ts
    namespace:"text", //model的命名空间是text
    state:{         //状态   
    }
```
2. state  
初始值  
3. reducers 
以```key/value```格式定义```reducer```用于处理同步操作，是唯一可以修改```state```的地方，由```action```触发。  
```ts
    reducers:{
        setState(state,payload){//state:自己定义的state，payload：组件传来需要修改的值
            return stat;//必须返回一个值，不然会报错的
        }
    }
```
4. effects
以```key/value```格式定义```effect```。用于处理异步操作和业务逻辑，不直接修改```state```，由```action```触发，可以触发```action```，可以和服务器交互，可以获取全局```state```的数据等等
```ts
    effects:{
        *setStateAny({payload},{call,put}){//call是发异步的
            yield put({
                type:'setState',
                data:{
                    name:''
                }
            })
            yield
        }
    }
```
5. subscriptions
以```key/value```格式定义```subscription```。```subscription```是订阅，用于订阅一个数据源，然后根据需要```dispatch```相应的```action```。在```app.start()```时被执行，数据源可以是当前时间，服务器的```websocket```连接、```keyboard```输入、```geolocation```变化、```history```路由变化等等。
```ts
    subscriptions:{
        haha({dispatch,history}){//dispatch是调用reducers里的方法
            history.listen(({pathname})=>{
                if(pathname==="/路径"){
                    
                }
            })
        }
    }
```
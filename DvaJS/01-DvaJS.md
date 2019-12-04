# DavJS
dva首先是一个基于redux和redux-saga的数据流方案，为了简化开发体验，dva还额外内置了react-router和fetch，所以也可以将dva理解为一个轻量级的应用框架。  
```ts
    https://dvajs.com/guide/introduce-class.html //学习网站
    https://github.com/dvajs/dva //github
```
# 搭建
## 安装dva-cli
**确保所安装的dva-cli的版本是0.9.1或以上**  
```ts
    npm install dva-cli -g  
    dva -v  //查看版本号  
```  
## 创建应用
```ts
    dva new test//test是目录名  
    cd test  //切换到新建的目录下面
    npm start //启动目录 
```
## 目录分析
```ts
    test  
        >mock  // 当服务端还没有接口时，用来模拟数据
        >node_modules
        >public //生成dist的静态目录  
            index.html
        >src //编辑的部分  
            >assets //静态的图片、资源
            >components //通用的组件
            >models  //放redux
            >routes     //配置路由的页面
            >sercices  //定义接口
            >utils  //放request （暴露给接口使用）
            index.css
            index.js
            router.js
        .editorconfig
        .eslitrc
        .gitgnore
        .roadhogrc.mock.js
        .webpackrc
        package-lock.json
        package.json
```
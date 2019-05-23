# React
- 主流前端框架设计模式基本都是MVVM,MVVM 由 Model、View、ViewModel 三部分构成，Model 层代表数据模型，也可以在Model中定义数据修改和操作的业务逻辑；View 代表UI 组件，它负责将数据模型转化成UI 展现出来，ViewModel 是一个同步View 和 Model的对象(可认为逻辑部分,Model变更,调用ViewModel 逻辑去render View UI)。
- View 和 Model 之间并没有直接的联系，而是通过ViewModel进行交互，Model 和 ViewModel 之间的交互是双向的， 因此View 数据的变化会同步到Model中，而Model 数据的变化也会立即反应到View 上。
## redux(本身与react没有任何关系,是react使用这个社区) 状态管理工具
### 概述
- 一个存放共享数据(store)的仓库，store收某些事件(action),想要修改store,必须发送action，才能去修改它，store对事件的响应，就是修改状态。
- 事件为action,修改状态的函数为reducer。

## Mobx
### 概述
- 状态管理工具
- observable,autorun 由 'mobx'提供，observable可以是store作为被观察的对象,autorun可以监听数据变化进行相对于的操作
  - //observable
  - const counter=observable({
    - count:0 
  - })
   - //autorun
   - window.count=counter
   - autorun(()=>{
     - //count变化执行下面
     - console.log('#count',counter.count)
   - })
  
- #### 案例
  - #### store
    - const counter=observable({
      - count:0 
    - })

    - counter.increment=fuction(){
        - this.count++
    - }
    - counter.decrement=fuction(){
        - this.count--
    - }
  - #### 组件
    - import {observer} from 'mobx-react'
    - @observer // 装饰必须要 固定写法
    - class xxx extends Component{
      - xxx
      - onIncerment(){
        - counter.increment()
      - }
      
    - }
  
  ## redux 与 mobx 区别
  - redux 原则只鼓励有一个store, mobx是多个。
  - redux 使用拉的方式使用数据与react设计原则类似，mobx使用推得方式使用数据与rxjs类似。
  - redux 代码范式化，减少代码，mobx代码容许代码多余，同时保证数据一致化
  ### 项目怎么选择用哪个？
  - redux:中大型、数据结构复杂、后期维护
  - mobx:中小型、快速开发、数据轻、结构简单
  
  ## hooks
  ### useContext,useEffect,useState,useReducer 后续
  
  ## 重写 this.props.children 让父组件托管state
  ### 案例
  #### 父组件render中的代码：
  -  统一传递this.props.numberIndex 、this.props.clickHandler给子组件中
     - const newElement=React.Children.map(this.props.children,(child,index)=>{
         - if(child.type){
         -   //克隆新的react的组件
           -   return React.cloneElement(child,{
               -     numberIndex:this.state.active===index,
               -     clickHandler:()=>this.setState({active:index})
           -   })
         - }else{
            -   return child
         - }
     - }))
     
     - return(
       -  \<Fragment>
            - {newElement}
       -  \</Fragment>
     - )
  
     #### 子组件
     - const Item=props=>{
         - const {numberIndex,clickHandler}=props;
         - return(
            -   xxx
         - )
     - }

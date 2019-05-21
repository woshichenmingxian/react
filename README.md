# React
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
  
- 

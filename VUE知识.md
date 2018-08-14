### 一、VUE的数据绑定（原理）

**vue不支持IE8以下浏览器的原因：**把一个普通对象传给 Vue 实例作为它的 data 选项，Vue.js 将遍历它的属性，用 Object.defineProperty 将它们转为 getter/setter。这是 ES5 特性，不能打补丁实现 

**用这个特性实现这样的功能，我们需要做什么呢？**

- **首先，需要利用Object.defineProperty，将要观察的对象，转化成getter/setter，以便拦截对象赋值与取值操作，称之为Observer；**
- **需要将DOM解析，提取其中的指令与占位符，并赋与不同的操作，称之为Compiler；**
- **需要将Compile的解析结果，与Observer所观察的对象连接起来，建立关系，在Observer观察到对象数据变化时，接收通知，同时更新DOM，称之为Watcher；**
- **最后，需要一个公共入口对象，接收配置，协调上述三者，称为Vue;**

**数据劫持: **   vue.js 则是采用数据劫持结合发布者-订阅者模式的方式，通过Object.defineProperty()
 来劫持各个属性的setter ，getter ，在数据变动时发布消息给订阅者，触发相应的监听回调。

**已经了解到vue是通过数据劫持的方式来做数据绑定的，其中最核心的方法便是通过Object.defineProperty()**
 **来实现对属性的劫持，达到监听数据变动的目的，无疑这个方法是本文中最重要、最基础的内容之一，要实现mvvm的双向绑定，就必须要实现以下几点：**
 **1、实现一个数据监听器Observer，能够对数据对象的所有属性进行监听，如有变动可拿到最新值并通知订阅者**
**2、实现一个指令解析器Compile，对每个元素节点的指令进行扫描和解析，根据指令模板替换数据，以及绑定相应的更新函数**
 **3、实现一个Watcher，作为连接Observer和Compile的桥梁，能够订阅并收到每个属性变动的通知，执行指令绑定的相应回调函数，从而更新视图**

**4、mvvm入口函数，整合以上三者**

 

## 二、实现Observer过程

1.转化getter/setter

 Observer是将输入的Plain Object进行处理,利用Object.defineProperty转化为getter与setter,从而在赋值与取值时进行拦截 这是Vue响应式框架的基础 

2.监听队列

​       现在我们已经可以拦截对象的getter/setter，也就是对象的赋值与取值时我们都会知道，知道后需要通知所有监听这个对象的Watcher，数据发生了改变，需要进行更新DOM等操作，所以我们需要维护一个监听队列，所有对该对象有兴趣的Watcher注册进来，接收通知。这一部分之前看了Vue的实现，感觉也不会有更巧妙的实现方式了，所以直接说一下实现原理。

- 首先，我们拦截了getter；
- 我们要为a.d添加Wacher监听者tmpWatcher；
- 将一个全局变量赋值target=tmpWatcher；
- 取值a.d，也就调用到了a.d的getter；
- 在a.d的getter中，将target添加到监听队列中；
- target = null;

​       就是这么简单，至于为什么可以这样做，是因为JS在浏览器中是单线程执行的！！所以在执行这个监听器的添加过程时，决不会有其他的监听器去修改全局变量target！！

3.实现Compiler



## 三、基本架构的介绍

![1533018359660](C:\Users\Administrator\AppData\Local\Temp\1533018359660.png)

如上图所示（除dist外，README.md是介绍，通过npm install安装的node_module中有些配置需要修改） 

1） build和config文件主要是webpack打包和端口的信息配置 

2） dist是打包以后才会生成的文件（npm run build执行此命令） 

3） node_modules是webpack的依赖模块，在node中使用npm install命令进行安装 

4） static文件夹主要放的是一些静态资源。（CSS+JS+IMG+JSON+fonts等） 

5） src 主要放的是你当前项目文件,一般是由组件+模块组成





## 四、基本组件的使用



```
new Vue({
        el,   //要绑定的DOM element
        data,  //要绑定的资料
        props,  //可用来接收父原件资料的属性
        template,  //要解析的模板，可以是#id , HTML 或某个DOM element 实体
        computed,  //定义资料的getter 与 setter,即需要计算后才能使用的属性
        components, //定义子元件，可用ES6简写法 例如（MyHeader）
        methods,  //定义可以在元件或样版内使用的方法
        propsData, //存放预设的props 内容，方便测试用
        relplace, //要不要用template取代el指向的DOM Element预设为ture
})
```

#### 这里说一下v-if和v-show的差别

`v-if`与`v-show`最大的差别在于对DOM的操作，v-if会依照条件决定是否将原件渲染至网页上，并决定时间于材料的监听是否要绑定至原件或直接销毁该原件。

`v-show`则是必定会产出原件，但以条件来切换css（style）的现实与否，若条件改变频繁，用`v-show`来切换更适合。

![20170503003839750](C:\Users\Administrator\Desktop\20170503003839750.jpg)

#### 这里在解释一下`method`和`component`以及`slot`

`<b>methods:</b>`一次加载一个数据 
`<b>component:</b>`一次加载多个数据,相当于属性的一个实时计算，如果实时计算里关联了对象，那么当某个值改变的时候，同时会发出实时计算。 
`<b>slot:</b>`使用`slot`分发内容，他的作用主要是为了让组件组件之前可以进行组合（混合父组件的内容和子组件自己的模板，这个过程叫做内容`<b>分发</b>）` 
`<slot>`的意思是插槽，插入的内容是从父组件传进来的,浅显点说就是提前站好坑，等需要用的时候，在过来用，好比老爹和儿子去吃饭，吃饭前，老爹要去上厕所，让儿子去占好餐桌，等老爹回来后，二人在一起吃。`<slot>`就是外部调用时，标签中的内容。如果外部调用时没有提供内容的话，那么它就会使用自己默认的内容。举一个例子说明：

```javascript
<template> 
    <div> 
      <slot name="CPU">这儿插你的CPU</slot> 
      <slot name="GPU">这儿插你的显卡</slot>
   </div> 
</template>
```

假设有个组件computer

```javascript
<template>
    <computer>
        <div slot="CPU">Intel Core i7</div> 
        <div slot="GPU">GTX980Ti</div> 
    </computer>
</template>
```




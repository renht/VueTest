Vue:
简介：MVVM框架
    核心：数据绑定
        组件
    借鉴Angular的模板和数据绑定技术
    借鉴react的组件化和虚拟DOM技术
优点：体积小，运行效率高，编码简洁，PC/移动都适合，本身值关注UI，可引入vue插件和其他第三方库。

基本使用：
    引入vue.js
    创建Vue对象（vm），指定配置对象
        el：指定DOM标签容器的选择器
        data：指定初始化状态数据的对象
              vue对象可直接访问其属性
              页面中可直接访问使用
              数据代理：vm对象来代理data中所有属性的操作
        methods：包含多个方法的对象
                公页面中的事件绑定回调
                回调函数默认由event参数，也可以自己制定参数
                所有方法由vue对象调用，访问data中的属性直接使用this.xxx
        computed:包含多个方法的对象
                对状态属性进行计算返回新的数据，供页面使用
                一般情况下是一个只读的属性
                利用set/get方法实现属性数据的计算读取，同时监视属性数据的变化
        watch：
            Vue.$watch()
                包含多个属性监视的对象
                分为一般监视和深度监视
            'XXX':{
                deep:true,
                handler:fun(value)
            }
    页面中
        v-model：实现双向数据绑定
        {{}}：表达式显示数据
页面指令：
    v-text/v-html：指定标签体
    v-text:当做纯文本
        v-html:将value作为html标签来解析
    v-if  v-else  v-show
        v-if:若value为true，当前抱歉会出现在页面中
        v-else：若value为false，当前标签输出到页面中
        v-show：会在标签中添加display样式，若value为true，display = block，若为false，则是none
            切换多个元素时，用template标签包裹
    v-for：遍历
        遍历数组：v-for="(person,index) in persons"   //index
        遍历对象：v-for="(value,key) in person"       //key
    v-on ：绑定事件监听
        v-on :事件名，可简写：@事件名
        监视具体的按键:@keyup.keyCode @keyup.enter
        阻止事件的冒泡和事件默认行为:@click.stop  @click.prevent
        隐含对象：$event
    v-bind:强制绑定解析表达式
        很多属性不支持表达式，可使用v-bind
        可简写：  :href="url"
        :class
            :class="a"
            :class="{classA : isA,classB :isB}"  isA/isB是boolean
            :class="['classA','classB']"         classA/classB 是字符串
        :style
            :style="{color:colorA}"              color：是样式名，colorA：样式值
    v-model
        双向数据绑定
    ref：标识某个标签
        ref = "xxx"
        读取得到标签对象：this.$refs.xxx
方法与事件处理器
      .prevent : 阻止事件的默认行为 event.preventDefault()  @click.prevent
      .stop : 停止事件冒泡 event.stopPropagation()         @click.stop
    按键修饰符
      .keyCode : 操作的是某个keycode值的健
      .enter : 操作的是enter键             @keyup.enter
        
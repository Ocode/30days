了解使用Polymer
===============

我学习的内容使用了 polymerchina.org 的slide并在小组内做了个技术分享，最后展示了官方 tutorial 实例，参看

[学习内容的slide](https://github.com/Ocode/gdg14/tree/dev)

之后整合转移到 [polymer-proj](https://github.com/Ocode/polymer-proj) 继续学习

发现一篇文章总结的不错，也分享给大家下

====================  华丽的分割线  ========================

这里是转载的译文

转载：[Polymer使用经验分享](http://www.topthink.com/topic/2673.html)

## Polymer使用经验分享

polymer 一个google开发的web components方式的前端UI控件库，它实现了google最新发布的Material design 设计规范。polymer的概念很超前，polymer中有很多可以借鉴学习的地方。

最近使用polymer对竞鹿官网进行改版， 将使用polymer的经验总结一下分享给大家。

## polymer是什么：

polymer 一个google开发的web components方式的前端UI控件库，它实现了google最新发布的Material design 设计规范。polymer的概念很超前，polymer中有很多可以借鉴学习的地方。 

polymer官方网站： http://www.polymer-project.org/

## 使用polymer的问题。

### web components 是什么
  
components 是组件的意思。

web组件就是web的一个一个元素标签， 如input标签，img标签，video标签等等。web componts 的概念就是把所有可重用的东西封转成元素组件，下次要用，自己使用自己写好的标签即可。polymer给大家提供了封装自定义标签的方法， 它自己也有很多已经封装的标签，如滑块：paper-slider,文档地址 http://www.polymer-project.org/docs/elements/paper-elements.html#paper-slider ，大家可以看看这个文档中的demo查看效果。

polymer的理念是一切功能切元素，即使是ajax，也是元素，core-ajax标签可以发起ajax请求，文档地址：http://www.polymer-project.org/docs/elements/core-elements.html#core-ajax

### 如何学习polymer

1) 看完get started的文档， 对polymer会有大体的了解 http://www.polymer-project.org/docs/start/getting-the-code.html

2)学习polymer自带标签的使用 http://www.polymer-project.org/docs/elements/ ， 

#### core-开头的是核心标签。

paper-开头的是Material design风格的标签。 paper-开头的标签会带有很炫的效果，它们一般是基于core-标签再此封装出来的。 比如paper-input标签 是基于 core-input封装的

### polymer 中如何选择新产生的dom元素。  

polymer选择元素的方法是  this.$.idname ， 可以选择模板中指定id的层。 但是这种选择方法不能选择新查询的层。 比如：

    &lt;template&gt; 
    &lt;div id="root"&gt;
        &lt;div id="a"&gt;A层&lt;/div&gt;
        &lt;template if="{{show_b}}"&gt;
        &lt;div id="b"&gt;B层&lt;/div&gt;
        &lt;/template&gt;
        &lt;div id="c"&gt;C层&lt;/div&gt;
     &lt;/div&gt;
    &lt;template&gt;
   
加上show_b这个变量默认值是false， 也就是说默认 不会有B层元素， 后面show_b变量为true是才会产生B层元素， 也就是说B层元素是后来生成的， 而不是初始化时就有的。

这时候我们在polymer代码中 可以用  this.$.a选择到A层， 可以用this.$.c选择到C层，但是无法用 this.$.b选择到B层。

**解决方法**是，我们可以在最外面加一个 root层， root层是初始化时就有的层， 因为B层是新生的，可以这样选择：this.$.root.querySelector('#b')

### 事件监听 on-eventname 和addEventlistener的区别。

polymer提供了on-eventname属性来对事件进行监听， 如监听按钮的点击事件：
&lt;paper-button id="button" label="flat button" on-click="{{buttonClick}}"&gt;&lt;/paper-button&gt;    另外还可以用addEventlistener监听事件， 如

    this.$.button.addEventlistener('click',function(){
        alert('click');
        console.log(this);
    })

在两种监听方法是有区别的。

    on-eventname 方式监听， 在监听函数中 this 指向的是当前polymer对象。你可以用this来获得当前polymer对象的其他属性。
    而addEventlistener 在监听函数中 this 是当前元素。

### 如何选中模板中&lt;content&gt;标签中的内容。

参考文章 http://www.html5rocks.com/en/tutorials/webcomponents/shadowdom-301/ ， 这篇文章中说明了 &lt;content&gt;标签代表的元素并不属于 shadow dom的元素，而是属于外层元素。 

所以用选择外层元素来选择它就好，  在polymer代码中可以这样选择：  this.querySelector('#id')

### polymer中如何导入jquery 。

    我们可以建立一个 lib.html  代码是： &lt;script src="./jquery.js"&gt;&lt;/script&gt;
    
    然后在元素中导入 &lt;link rel="import" href="lib.html" /&gt;

因为 link import 加载的页面时会自动判定是否重复加载只会加载一次（类似php的require_once函数）。 所以及时我们在多个元素中 导入lib.html 都不会重复加载jquery 。

### polymer 兼容语法  

我们在CSS样式中，可以用/deep/ 语法，让一条元素既对html元素生效，也对shadow dom元素生效。 如：

    html /deep/ h3 { background:red }

但是deep语法，并非所有浏览器都支持。 兼容不支持deep语法的浏览器的方法，

link标签导入样式时，加上shim-shadowdom属性  

    &lt;link rel="stylesheet" href="./xxx.css" shim-shadowdom /&gt;

style标签定义元素时，加上shim-shadowdom 属性

    &lt;style  shim-shadowdom&gt;
    &lt;/style&gt;

这其实是在告诉polymer的平台兼容js，这些地方需要处理， platform.js会识别到这些区域，然后用js做兼容处理。

我们在css中还经常会用 ::content 选择 &lt;content&gt; 标签指定中的元素， 但是 ::content 语法也是一些浏览器不支持的， 所以要用polyfill-next-selector在声明一下， 如： 

    polyfill-next-selector { content: '#question .title:before'; } 
    #question ::content .title{
        //css样式代码
    }

### 文件的相对路径 

polymer中的相对路径一般都是相对于当前文件的路径，而不是相对于入口文件的路径，这个大家用过polymer都知道，比如 link import 导入文件时就是这样的。

大家要注意的是，如果你自定义元素中有和地址相关的属性，polymer也会自动给你计算出当前文件的相对路径。 如：

我们在 /element 文件下建立 my-element.html 定义一个元素，代码如下：

    &lt;polymer-element name="my-element" attributes="url"&gt;
        &lt;script&gt;
            Polymer('my-element',{
                ready:function(){
                    alert(this.url);
                }       
             });
        &lt;/script&gt;
    &lt;/polymer-element&gt;

上面元素定义了一个url属性，并在初始化时alert出url属性的值。

然后我们在另外一个页面调用这个元素，假设另外一个页面地址是 /page/test.html , 调用代码如下：  

    &lt;my-element url="p/a/t/h"&gt;&lt;/my-element&gt;

我们运行代码发现， alert出来的字符串被处理了，  打印出的字符串是  page/p/a/t/h ，  注意不是 p/a/t/h,也不是 element/p/a/t/h

这些属性名称会被polymer计算相对地址： url,href,src 。 如果你自定义元素有自定这些属性要注意了。 你如果不想polymer给这些属性自动加上计算的目录结构， 你只能以斜杆开头定义一个绝对路径。

### ajax传参技巧 

core-ajax 传递的params参数 可以直接和输入框对应上， 如：

    &lt;core-ajax id="ajax" url="http://url" params="{{formdata}}" method="post" &gt;&lt;/core-ajax&gt;

然后有提交表单的输入框：

    &lt;paper-input  inputValue="{{formdata.email}}" /&gt;
    &lt;paper-input  inputValue="{{formdata.name}}" /&gt;

这里的这个formdata 需要初始化声明是一个对象， 不然写会报错的。

    Polymer('my-elementer',{
        //这里声明一个formdata对象，空的都行，但是不声明不行。
        formdata:{}
    })

### layout 布局


polymer layout布局功能， 是用flex实现的， 比较先进，还能实现元素的垂直居中。 但现在支持的浏览器较少，等以后浏览器都先进了，可以过来看看polymer的实现代码借鉴一下。

文档地址 http://www.polymer-project.org/docs/polymer/layout-attrs.html

代码在：polymer/layout.html 文件中。

### polymer的原理。

polymer自定义标签，建立一个新元素，然后定义元素的shadow dom， shadow dom是HTML5  的内容， 详见：  http://www.html5rocks.com/en/tutorials/webcomponents/shadowdom/

定义好自定义元素后是用 link import导入的， link import 也是HTML5 的知识 , 详见： http://www.html5rocks.com/en/tutorials/webcomponents/imports/

用了这么多HTML5的技术，一些浏览器不支持的， 所以要在用polymer之前，加载platform.js，然后不支持这些HTML5特性的浏览器可以用js来实现兼容。 

但它兼容性有些差，对android版本要求4.3以上。 因此，对应国内来说， 大部分android用户 访问有问题， 因此polymer也不能用到phonegap中， 这是polymer比较遗憾的地方。但是不影响我们去学习和借鉴它的一些东西。 

### polymer一次导入的文件太多，能否压缩。

polymer 每使用一个标签，都要导入一个文件，而且标签可能还有依赖，所以polymer代码写完后，我们发现页面加载了好多文件， 能否压缩优化，让一次加载？

这是可以的，使用 https://github.com/Polymer/vulcanize

因为polymer兼容性的问题，最后我们还是换回了angularjs做官网。

我们之前写的polymer代码大家可以借鉴一下， 地址是： http://5.deersite.sinaapp.com/


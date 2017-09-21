#前端面试体汇总

##CSS类
###1、假设高度已知，请写出三栏布局，其中左栏、右栏宽度各为300px，中间自适应。（请写出五到七种方案，并说出各种方案的优缺点和兼容性）

- html结构
```
<div class="oDiv">
    <div class="left">left</div>
    <div class="center">center</div>
    <div class="right">right</div>
</div>
```
####方法一(绝对定位)
- css样式
```
    <style>
        * {
            margin: 0;
            padding: 0;
        }

        .oDiv {
            height: 300px;
            line-height: 300px;
            padding-left: 300px;
            padding-right: 300px;
            text-align: center;
            position: relative;
            background-color: lightseagreen;
        }

        .left{
            width: 300px;
            height: 300px;
            position: absolute;
            left: 0;
            top: 0;
            background-color: lightsalmon;
        }

        .right{
            width: 300px;
            height: 300px;
            position: absolute;
            right: 0;
            top: 0;
            background-color: lightpink;
        }
    </style>
```
![Alt text](./1505960692768.png)
> 绝对定位：
> 该方法有个明显的缺点，就是如果中间栏含有最小宽度限制，或是含有宽度的内部元素，当浏览器宽度小到一定程度，会发生层重叠的情况。




####方法二(浮动)
```
<div class="oDiv">
    <div class="left">left</div>
    <div class="right">right</div>
    <div class="center">center</div>
</div>
```
- css样式
```
       .left,.right{
            width: 300px;
            height: 300px;
            background-color: lightpink;
        }

        .left{
            float: left;
        }

        .right{
            float: right;
        }

        .center{
            margin: 0 300px;
            height: 300px;
            background-color: lightskyblue;
        }
```
![Alt text](./1505961366051.png)

> 浮动法:
> 原理就是使用对左右使用分别使用float:left和float:right，float使左右两个元素脱离文档流，中间元素正常在正常文档流中，使用margin指定左右外边距对其进行一个定位
> 
> 需注意：
> center一定要放在最后，这是和绝对定位不一样的地方，center占据文档流位置，所以一定要放在最后，当浏览器窗口很小的时候，left会被挤到下一行

####方法三(给定位负值)
- css样式
```
.oDiv {
            position: relative;
            margin-left: 300px;
            margin-right: 300px;
            height: 300px;
            background-color: lightgoldenrodyellow;
        }

        .left {
            width: 300px;
            position: absolute;
            left: -300px;
            height: 300px;
            background-color: lightsalmon;
        }

        .right {
            width: 300px;
            position: absolute;
            right: -300px;
            height: 300px;
            background-color: lightseagreen;
        }
```
![Alt text](./1505961757298.png)

>给left和right定位负值
    

####方法四(flex布局)
- css样式
```
      .oDiv{
            width: 100%;
            height: 300px;
            display: flex;
        }

        .left,.right{
            width: 300px;
            height: 300px;
            background-color: lightgreen;
        }

        .center{
            flex: 1;
            height: 300px;
            background-color: lightcyan;
        }
```
![Alt text](./1505962048984.png)

> 置为display：flex；中间设置flex：1

####方法五(给center也定位)
- css样式
```
.oDiv{
            position: relative;
        }

        .left {
            width: 300px;
            position: absolute;
            left: 0;
            height: 300px;
            background-color: lightseagreen;
        }

        .center {
            position: absolute;
            left: 300px;
            right: 300px;
            height: 300px;
            background-color: lightsalmon;
        }

        .right{
            width: 300px;
            position: absolute;
            right: 0;
            height: 300px;
            background-color: lightgoldenrodyellow;

        }

```
![Alt text](./1505962587801.png)


###2、左侧菜单栏占300px，右侧内容可以根据浏览器自适应。根据此要求，编写html css代码

```
<!DOCTYPE>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .oDiv{
            line-height: 300px;
            text-align: center;
        }

        .left {
            float: left;
            height: 300px;
            width: 300px;
            background-color: lightsalmon;
        }
        .right {
            overflow: auto;
            height: 300px;
            background-color: lightpink;
        }
    </style>
</head>
<body>
<div class="oDiv">
<div class="left">固定</div>
<div class="right">自适应</div>
</div>
</body>
</html>
```
![Alt text](./1505969417470.png)


###3、CSS选择器又哪些？有哪些新特性？有哪些伪类？
- css选择器 共12个
   - 标签选择器
   - 类选择器
   - id选择器
   -  属性选择器
   -  分组选择器
   - 交集选择器
   -  通配符选择器
   -  后代选择器
   -  子级选择器
   - 相邻选择器
   -  伪类选择器
   - 伪元素


----------


- css选择器的新特性
- CSS3
新增各种CSS选择器     `: not(.input)：所有 class 不是“input”的节点 `
 圆角                            `border-radius:8px`
多列布局                     `multi-column layout`
 阴影和反射                `Shadow\Reflect`
文字特效                     `text-shadow`
文字渲染                    `Text-decoration `
线性渐变                    `gradient `
旋转                           `transform`
增加了旋转,缩放,定位,倾斜,动画，多背景
`transform:\scale(0.85,0.90)\ translate(0px,-30px)\ skew(-9deg,0deg)\Animation`


----------
- css有哪些伪类
- :root 选择元素所在文档的根元素
- :not（）否定选择器
- :empty 用来选择没有任何内容的元素
- F : first-child 选择F的第一个子元素(所有第一个子元素都会被选择) 
- :last-child 选择最后一个子元素
- :nth-child(n) 用来定位某父元素的一个或多个特定的子元素
- :nth-last-child(n) 选择在其父元素中倒数第n个位置的元素或特定某元素
- :first-of-type 父元素下的某个类型的第一个子元素
- :last-of-type 选择是父元素下的某个类型的最后一个子元素
- :nth-of-type(n)只计算父元素中指定的某种类型的子元素
- :only-child 有且仅有一个子元素 

其他的常见伪类选择器
- :link表示未访问的超链接
- visite表示已访问的
- :hover 鼠标移动到容器
- :active 被激活时的状态
- :focus 用于设置获取焦点时的样式
- :read-only用来指定处于只读状态元素的样式
- :read-write 用来指定当元素处于非只读状态时的样式


###4、清除浮动的几种方式，优缺点

清除浮动的4种方式:
1.給浮动元素的父元素加高度 height
> 原理：父级div手动定义height，就解决了父级div无法自动获取到高度的问题
优点：简单，代码少，容易掌握
缺点：只适合高度固定的布局，要给出精确的高度，如果高度和父级div不一样时，会产生问题

2.給浮动元素的父元素加overflow:hidden;
>优点：简单，代码少，浏览器支持好
缺点：不能和position配合使用，因为超出的尺寸的会被隐藏

3.給浮动元素的父元素结束标签之前加一个空div  <div  style="clear:both"></div>
>原理：添加一个空div，利用css提高的clear:both清除浮动，让父级div能自动获取到高度
优点：简单，代码少，浏览器支持好，不容易出现怪问题
缺点：不少初学者不理解原理；如果页面浮动布局多，就要增加很多空div，让人感觉很不爽

4.給浮动元素的父元素加一个class名 clearfix; 把清浮动的样式放到reset.css/reset.min.css 样式表中 
  <div class="clearfix"></div>
![Alt text](1505965180170.png)

###5、图片如何实现垂直居中的
> 将外部容器的显示模式设置成display:table， img标签外部再嵌套一个span标签，并设置span的显示模式为`display:table-cell`，这样span内部的内容就相当于表格，可以很方便的使用`vertical-align`属性来对齐其中的内容了

###6、css hack你知道哪些？
为了获得统一的页面效果，需要针对不同的浏览器或不同版本写特定的CSS样式，我们把这个针对不同的浏览器/不同版本写相应的CSS code的过程，叫做CSS hack

Css Hack 特殊符号
（1）* ：IE6/7都能识别*，标准浏览器不识别
（2）_：只有IE6识别
（3）！Important：IE6不识别，Firefox，IE7/8/9、chorme等主流浏览器均识别
（4）\9：所有浏览器均识别，包括IE6/7/8
（5）+：IE6/7/8识别
（6）书写顺序：先写FF等非IE浏览器所需样式，其次IE8，再次IE7，最后写IE6


###6、谈谈你对CSS盒模型的认识

####标准模型和IE模型的区别?
```
计算宽度和高度的不同
标准模型的宽高：是content -->width
IE模型的是包括 content + border + padding
```

详细解释：
> 标准 W3C 盒子模型的范围包括 margin、border、padding、content，并且 content 部分不包含其他部分
> IE 盒子模型的范围也包括 margin、border、padding、content，和标准 W3C 盒子模型不同的是：IE 盒子模型的 content 部分包含了 border 和 pading

```
网页中的盒子模型；我们常常要控制盒子模型的宽度width:   
w3c中的盒子模型的宽:包括margin+border+padding+width;
 width:margin*2+border*2+padding*2+width;
height:margin*2+border*2+padding*2+height;

iE中的盒子模型的width:
也包括margin+border+padding+width;

上面的两个宽度相加的属性是一样的。不过在ie中content的宽度包括padding和border这两个属性；

例如一个盒子模型如下：margin:20px,border:10px,padding:10px;width:200px;height:50px;
如果用w3c盒子模型解释，那么这个盒子模型占用的
宽度为：20*2+10*2+10*2+200=280px; 
高度：20*2+10*2+20*2+50=130px;
盒子的实际宽度大小为:10*2+10*2+200=240px;
实际高度：10*2+10*2+50=90px;

用ie的盒子模型解释 ：盒子在网页中占据的大小为20*2+200=240px; 高：20*2+50=90px;
盒子的实际大小为：宽度:200px, 高度:50px;
我们常常理解的盒子模型是w3c这样的盒子模型
```
----------


####CSS是如何设置这两种模型?
```
标准：box-sizing:content-box
IE：  box-sizing:border-box
```
----------

####JS如何设置和获取盒模型对应的宽和高?
```
(1).dom.style.width/height
(2).dom.currentStyle.width/height 拿到渲染后的数据 只有IE支持
(3). window.getComputedStyle(dom).width/height 用这个 兼容性好
(4).dom.getBoundingClientRect().width/height
```
----------

####什么是优雅降级和渐进增强?
```
.transition{
  -webkit-transition: all .5s;
     -moz-transition: all .5s;
       -o-transition: all .5s;
          transition: all .5s;  
}
```

```
.transition{ 
　　     transition: all .5s;
　　  -o-transition: all .5s;
  　-moz-transition: all .5s;
 -webkit-transition: all .5s;
}
```

transition放在前面还是后面却引申了两个概念：优雅降级和渐进增强。

>优雅降级和渐进增强印象中是随着css3流出来的一个概念。由于低级浏览器不支持css3，但css3的效果又太优秀不忍放弃，所以在高级浏览中使用css3而低级浏览器只保证最基本的功能。咋一看两个概念差不多，都是在关注不同浏览器下的不同体验，关键的区别是他们所侧重的内容，以及这种不同造成的工作流程的差异。


什么是渐进增强（progressive enhancement）、优雅降级（graceful degradation）呢？

- 渐进增强 progressive enhancement：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。

- 优雅降级 graceful degradation：一开始就构建完整的功能，然后再针对低版本浏览器进行兼容。

- 区别：优雅降级是从复杂的现状开始，并试图减少用户体验的供给，而渐进增强则是从一个非常基础的，能够起作用的版本开始，并不断扩充，以适应未来环境的需要。降级（功能衰减）意味着往回看；而渐进增强则意味着朝前看，同时保证其根基处于安全地带。

----------

###6、谈谈你对BFC的了解

####什么是BFC?

>BFC(Block formatting context)直译为"块级格式化上下文"。它是一个独立的渲染区域，只有Block-level box参与， 它规定了内部的Block-level Box如何布局，并且与这个区域外部毫不相干。

>通俗讲，BFC就是一种布局方式，在创建了 BFC后，其子元素会一个接一个地放置：盒子们自所在的 containing block 顶部起，水平方向上一个接一个撑满整个宽度，垂直方向上他们的起点是包含块的顶部，两个相邻的元素之间的垂直距离取决于 ‘margin’ 特性。在 同一个BFC中，两个元素才有可能发生垂直Margin的重叠，这个包括相邻元素，嵌套元素，只要他们之间没有间隔(即父元素的边框，非空内容，padding等)就会发生margin重叠，即margin会发生重合。更重要的是：创建BFC,能消除元素对相邻元素的布局影响，常见的应用 是：使用overflow:hidden创建BFC ,来清除浮动元素对后面元素的布局影响 。


----------



####如何创建BFC?
当一个HTML元素满足下面条件的任何一点，都可以产生BFC：

常见的：
1. float的值不为”none” (如：float:left/right)

1. overflow的值不为”visible”(如：overflow:hidden)

1. display的值为 “table-cell”, “table-caption”, or “inline-block”中的任何一个

1. position的值不为 “static” 或 “relative”中的任何一个(如：position:absolute)

```
为下情况都会让元素本身产生BFC环境：

·根元素 (一个页面的Html标签应该是唯一的)
·display: inline-block | table-cell | table-caption | flex
· position: absolute | fixed
· overflow: hidden | auto | scroll
· float: left | right
```
----------


####BFC使用场景?
>BFC的主要作用有以下几点：
- 边距重叠
- 不与float box重叠
- 高度塌陷

详情：http://www.cnblogs.com/HCJJ/p/6263075.html


##JS类
###1、DOM事件

#### DOM事件级别有哪些?
>DOM 0级  和  DOM 2级事件

----------


####描述DOM事件捕获和冒泡的具体流程?
`事件捕获 先捕获--->再到目标--->再到冒泡`
```
1.捕获阶段：先由文档的根节点document往事件触发对象，从外向内捕获事件对象；
  
2.目标阶段：到达目标事件位置（事发地），触发事件；
  
3.冒泡阶段：再从目标事件位置往文档的根节点方向回溯，从内向外冒泡事件对象。
```

----------


####Event对象的常见应用场景?
当事件触发的时候，浏览器默认会为处理函数传递一个参数
e 事件对象：是一个对数据类型的 存储着事件的相关信息
>我们根据事件对象中的事件源来判断 （当前是哪个元素）并作出相应的处理`e.target`
>阻止默认行为  `e.preventDefault();`
>阻止冒泡传播`e.stopPropagation();  `  
>
![Alt text](1505969520474.png)

----------


#### 事件委托是什么？
>事件委托：利用事件默认会进行冒泡传播的机制，给最外层容器相关行为（eg：click）绑定事件，当后代元素中的 相关行为（click）触发时，会一直触发到最外层容器相关行为（click） 我们根据事件对象中的事件源来判断 （当前是哪个元素）并作出相应的处理

----------


####事件冒泡,e.targe和e.currentTarget的区别

>事件传播（事件冒泡）：
当前元素的相关行为（例如click）触发的时候 ，他的所有上级元素的相关行为（click）也会触发  一直到document   （！行为要统一 如果一个是onclick一个是onmouseover  就不会有冒泡）

>e.targe和e.currentTarget的区别
>e.currentTarget指的是注册了事件监听器的对象，而e.target指的是该对象里的子对象，也是触发这个事件的对象！
详情：http://blog.csdn.net/ZYY88886666/article/details/76021880


####浏览器的兼容问题(js)
```
e=e||window.event;//事件对象兼容
e.target=e.target||e.srcElement;//事件源兼容
e.returnValue = false;  //阻止默认事件兼容
阻止冒泡传播兼容写法
e.stopPropagation();？e.stopPropagation()：e.cancelBubble=true;
```
![Alt text](1505970765369.png)


###2、JS原生

####JS中有哪些数据类型

>基本数据类型：number,string,boolean,null,undefined

>引用数据类型：函数数据类型  function
>对象数据类型：数组类，对象类，正则类，Date,Math

----------


####什么是闭包？闭包作用？在工作中是如何应用的?
>闭包的概念：函数执行都会形成一个私有作用域  保护里面定义的私有变量不受外界干扰，这种保护机制 叫做闭包
>闭包的作用：可以读取函数内部的变量，还可以让这些变量的值始终保持在内存中
>（1）逻辑连续，当闭包作为另一个函数调用参数时，避免脱离当前逻辑而单独编写额外逻辑。
（2）方便调用上下文的局部变量。
（3）加强封装性，是第2点的延伸，可以达到对变量的保护作用。
使用场景：
（1）采用函数引用方式的setTimeout调用。 例子
（2）将函数关联到对象的实例方法。
（3）封装相关的功能集。

----------


####JS实现继承的几种方式?
>1、原型链继承
>核心： 将父类的实例作为子类的原型
>
特点：非常纯粹的继承关系，实例是子类的实例，也是父类的实例
父类新增原型方法/原型属性，子类都能访问到
简单，易于实现
>
缺点：要想为子类新增属性和方法，必须要在new Animal()这样的语句之后执行，不能放到构造器中
无法实现多继承
来自原型对象的引用属性是所有实例共享的（详细请看附录代码： 示例1）
创建子类实例时，无法向父类构造函数传参


>2、构造继承
>核心：使用父类的构造函数来增强子类实例，等于是复制父类的实例属性给子类（没用到原型）
>
特点：解决了1中，子类实例共享父类引用属性的问题
创建子类实例时，可以向父类传递参数
可以实现多继承（call多个父类对象）
>
缺点：实例并不是父类的实例，只是子类的实例
只能继承父类的实例属性和方法，不能继承原型属性/方法
无法实现函数复用，每个子类都有父类实例函数的副本，影响性能

>3、实例继承
>
核心：为父类实例添加新特性，作为子类实例返回
>
特点：不限制调用方式，不管是new 子类()还是子类(),返回的对象具有相同的效果
>
缺点：实例是父类的实例，不是子类的实例 不支持多继承

>4、拷贝继承
> 特点：支持多继承
> 
缺点：效率较低，内存占用高（因为要拷贝父类的属性）
无法获取父类不可枚举的方法（不可枚举方法，不能使用for in 访问到）

>5、组合继承

>核心：通过调用父类构造，继承父类的属性并保留传参的优点，然后通过将父类实例作为子类原型，实现函数复用
>
特点：弥补了方式2的缺陷，可以继承实例属性/方法，也可以继承原型属性/方法
既是子类的实例，也是父类的实例    不存在引用属性共享问题    可传参    函数可复用
缺点：调用了两次父类构造函数，生成了两份实例（子类实例将子类原型上的那份屏蔽了）
>
6、寄生组合继承
核心：通过寄生方式，砍掉父类的实例属性，这样，在调用两次父类的构造的时候，就不会初始化两次实例方法/属性，避免的组合继承的缺点
特点：堪称完美
缺点：实现较为复杂

http://www.cnblogs.com/humin/p/4556820.html

----------


####创建对象的三种方式?
```
1.对象字面量创建对象
  
var obj = { a:1,b:2 };
  
注意：对象字面量是一个表达式，这种表达式每次运算都会创建并初始化一个新对象，并计算这个新对象的每个属性值。所以如果在循环体内使用对象字面量，每次循环时都会创建新对象。
  
2.通过new运算符创建对象
      var obj = new Object(); //创建空对象  var ary = new Array(); //创建空的数组对象    
注意：new运算符后面跟的是一个函数调用，这个函数被称为构造函数。js中原始类型都包含内置的构造函数，也可以自己定义构造函数。
  
3.通过立即执行函数创建对象
  
var obj = (function(){ return {x:1,y:2};}());
  
注意：在立即执行函数内部一定要有return语句，return出的内容就是待创建的对象。
  
4.通过Object.create()创建对象
  
var obj = Object.create({x:1,y:2});
  
注意：Object.create()是一个静态函数，传入原型对象就可以创建继承此原型对象的对象，例如上面的例子中obj对象继承了x,y属性。
```


####new Person()时发生了什么?
>构造函数模式执行  通过一个new 把Person 当做一个类 执行 并且返回这个类的实例     就是返回“Object”
>(构造函数模式：创建一个自定义类  并且创建这个类的实例（封装组件）)


#### 什么是深拷贝和浅拷贝？自己不用JSON.parse实现一个深拷贝的方法
>1.浅拷贝：复制一份引用，所有引用对象都指向一份数据，并且都可以修改这份数据。  
  2.深拷贝（复杂）：复制变量值，对于非基本类型的变量，则递归至基本类型变量后，再复制。
  深拷贝: 复制对象所引用的全部对象。  
  浅拷贝: 仅仅复制对象的引用,而不是对象本身。 

  
- 数组的slice  深拷贝  浅拷贝
浅拷贝  深拷贝
let obj={a:1};
[obj] [obj]    浅拷贝    里在存放的内容和以前的同一个地址
[obj] [{a:1}]  深拷贝   指的是对象中，里面存放的对象和以前的对象 豪无关系 但是长的一样 

`let obj2={...obj}`

----------


####手工模拟完整的bind方法
```
function myBind(context, fn) {
        return function (e) {
            fn.call(context, e)
        }
    }
```

----------


####什么是节流和防抖？
   - 函数节流：是确保函数特定的时间内至多执行一次。
   - 函数防抖：是函数在特定的时间内不被再调用后执行。
>应用场景：
>
函数节流（throttle）
1. 频繁的mousemove/keydown，比如高频的鼠标移动，游戏射击类的
2. 搜索联想（keyup）
3. 进度条（我们可能不需要高频的更新进度）
4. 拖拽的dragover等
5.  高频的点击，抽奖等
 >
函数防抖（debounce）
 1. scroll/resize事件
 2. 文本连续输入，ajax验证/关键字搜索

----------


####上拉刷新和下拉加载的实现原理？
>【1】Header
Header通常有下拉箭头，文字，进度条等元素，根据下拉的距离来改变它的状态，从而显示不同的样式
【2】Content
这部分是内容区域，网上有很多例子都是直接在ListView里面添加Header，但这就有局限性，因为好多情况下并不一定是用ListView来显示数据。把要显示内容的View放置在一个容器中，如果想实现一个用ListView显示数据的下拉刷新，需要创建一个ListView旋转到容器中。处理这个容器的事件（down，move，up），如果向下拉，则把整个布局向下滑动，从而把header显示出来。
【3】Footer
Footer可以用来显示向上拉的箭头，自动加载更多的进度条等。

----------


####写一个验证邮件的正则表达式
验证邮箱
monkey@qq.com
monkey@163.cn
monkey_seven@163.com.cn
数字 字母 下划线 @  数字 字母 {2,10}  . 点   字母 {2,3}
```
 var reg=/^\w+@[0-9a-z]{2,8}(\.[a-z]{2,8}){1,2}$/;
 console.log(reg.test("42424325@qq.com"));
```
![Alt text](1505981790974.png)

----------


####事件绑定和普通事件的区别（可以举例说明）
>`(“#panel”).bind(“click”,function(){`与`$(“#panel”).click(function(){`有什么区别 ？
绑定可以同时加多个事件
```
如：$(“#panel”).bind({“click”, “mousemove”, …})

$(“#panel”).click(function(){}这样是一次注册一个事件

bind(type,[data],fn)
```
为每一个匹配元素一个或多个事件绑定事件处理器函数
```
$(‘#foo’).bind({
click: function() {
// do something on click
},
mouseenter: function() {
// do something on mouseenter
}
});
```
你可以在事件处理之前传递一些附加的数据。
```
function handler(event) {
alert(event.data.foo);
}
$(“p”).bind(“click”, {foo: “bar”}, handler)

$(“#panel”).bind(“click”,function(){})
$(“#panel”).click(function(){})
```
这两个是相等的。第二种是第一种的简写。

----------


####javascript 模版引擎用过哪些？实现原理是什么？
>EJS(Embedded JavaScript)也是众多模板中的一种，它主要是NODE开源的模板，在NODE环境下实现绑定和渲染的。但是它也可以单独的在客户端调取使用。
>

----------


####合并两个对象
`es2015 Object.assign()`
```
var o1 = { a: 1 };
var o2 = { b: 2 };
var o3 = { c: 3 };

var obj = Object.assign(o1, o2, o3);
console.log(obj); // { a: 1, b: 2, c: 3 }
console.log(o1);  // { a: 1, b: 2, c: 3 }, 注意目标对象自身也会改变。
```


####动态向一个div中插入1000个div标签，如何实现？（考性能）
```
<body>
<div id="oDiv"></div>
<script>
    let oDiv=document.getElementById("oDiv");
    let str="";
    for(let i=0;i<10;i++){
        str+="<div></div>"
    }
    oDiv.innerHTML=str;
</script>
```


####html5新特性
```
1、拖拽释放(Drag and drop) API 
2、语义化更好的内容标签（header,nav,footer,aside,article,section）
3、音频、视频API(audio,video)
4、画布(Canvas) API
5、地理(Geolocation) API
6、本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；
7、sessionStorage 的数据在浏览器关闭后自动删除 
8、表单控件，calendar、date、time、email、url、search  
9、新的技术webworker, websocket, Geolocation
```


####严格模式和非严格模式的区别
>在严格（"use strict"）模式下  （要写在第一行）
>严格模式 让js在严格的条件运行js(消除不合理  一些怪异行为 优化编译器运行速度)
  ● 函数执行前面就算没有点 this指向的不是window 而是 undefined
  ● 自执行函数中的this也是undefined
  ● arguments 传的参就算在函数里修改 也不会改变  因为是在严格模式下
```

严格模式中，对象直接量中定义同名属性会抛出语法错误； 非严格模式不会报错
严格模式中，函数形参存在同名的，抛出错误； 非严格模式不会
严格模式不允许八进制整数直接量（如：023）
严格模式中 eval和arguments当做关键字，它们不能被赋值和用作变量声明
严格模式会限制对调用栈的检测能力，访问arguments.callee.caller会抛出异常
严格模式 变量必须先声明，直接给变量赋值，不会隐式创建全局变量，不能用with,
严格模式中 call apply传入null undefined保持原样不被转换为window
严格模式下, delete运算符后跟随非法标识符(即delete 不存在的标识符)，
          会抛出语法错误； 非严格模式下，会静默失败并返回false
严格模式中，arguments对象是传入函数内实参列表的静态副本；非严格模式下，
          arguments对象里的元素和对应的实参是指向同一个值的引用
```

----------


####对于js中浮点数计算会丢失精度的问题，你有什么解决思路？
>方法一
>指定要宝库小数位数（0.1+0.2）.toFixed(1)=0.3; 这个方法toFixed是进行四舍五入的也不是很精确，对于计算金额这种严谨的问题，不推荐使用，而且不通过浏览器对toFied的计算结果也存在差异
>方法二
>把需要计算的数字升级（乘以10的n次幂）成计算机能够精确识别的整数，等计算完毕再降级（除以10的n次宽幂），这是大部分编程语言处理精度差异的通用方法


##JQuery

####jquery.extend , jquery.fn.extend的区别
```
jquery.extend , jquery.fn.extend的区别
    jquery.extend({ //在jq的自身属性上扩展方法
        add(){}
    })
    jquery.extend(obj1,obj2)//合并对象，obj2合并到obj1中 ，有返回值

    jquery.fn.extend({//在jq原型上扩展方法
        add(){}
    })
```

####谈一下jquery中的bind，live，delegate，on区别
>  bind(type,[data],fn) 为每个匹配元素的特定事件绑定事件处理函数
        $("a").bind("click",function(){alert("ok");});
        live(type,[data],fn) 给所有匹配的元素附加一个事件处理函数，即使这个元素是以后再添加进来的
        $("a").live("click",function(){alert("ok");});
        delegate(selector,[type],[data],fn) 
        指定的元素（属于被选元素的子元素）添加一个或多个事件处理程序，并规定当这些事件发生时运行的函数
        $("#container").delegate("a","click",function(){alert("ok");})
        on(events,[selector],[data],fn) 在选择元素上绑定一个或多个事件的事件处理函数
    
```
.bind()是直接绑定在元素上
.live()则是通过冒泡的方式来绑定到元素上的。更适合列表类型的，绑定到document DOM节点上。和.bind()的优势是支持动态数据。
.delegate()则是更精确的小范围使用事件代理，性能优于.live()
.on()则是最新的1.9版本整合了之前的三种方式的新事件绑定机制
```


####document.ready和document.load和$(function(){})有什么区别？
> document.ready 是页面文件资源加载完毕 执行
   document.load 是dom结构详细信息（包括了加载图片等其他信息）加载完毕执行
    $(function(){}) dom结构加载完成 执行

####$.data()和$('#aaa').data()各自作用是什么？有什么区别
>$.data() 在元素上存放数据,返回jQuery对象。不会展现在html上
 $('#aaa').data() 获取自定义属性存储的信息

##ES6

####什么时候应该用箭头函数？什么时候不能用？ － 请写出ES6中Array.isArray()的实现代码
1. 使用剪头函数不需要敲完整的 function 关键字， 同时如果只有行 return 语句的函数，还可以进一步简写：
例如 要定义一个 trim 函数，不使用箭头函数：
```
        const trim = function( str ) {
            return trim.replace( /^\s+|\s+$/g, '' );
        };
        使用箭头函数：
        const trim = str => trim.replace(  /^\s+|\s+$/g, '' ); 
```
2. 在函数内部不需要自己的 this 指针的时候，非常方便，因为箭头函数作用域内没有 this
    例如下面不使用箭头函数的代码， 要通过将 this 赋值给 me，调用 me 来调用 Obj：
```
    const Obj = {
        text : 'ABC',
        replace : function( arr ) {
            var me = this;
            arr.forEach( function( item ) {
                return me.text;
            } );
        }
    };
    使用箭头函数：
    const Obj = {
        text : 'ABC',
        replace : function( arr ) {
            arr.forEach( item => this.text );
        }
    };
```

3. 还有一点是 箭头函数没有 arguments 变量。


----------


####如何在项目中解析处理es6和es7代码
- babel-core是babel的核心包，使用babel必须安装
- babel-loder是babel的翻译官 用来翻译语法的，但是他不懂
- 配置预设让他懂  es6 babel-preset-es2015
新建  `.babelrc`
`"presets":["es2015","stage-0"]`   给翻译官加技能  让他懂得es7
```
es语法一共有四个阶段 分别为 stage-3    stage-2     stage-1    stage-0 (0是最高的 里面语法最多)
0里面包含着  3   2   1等  所以安0就相当于安7了

npm install babel-preset-stage-0 --save-dev
```

----------

####Promise常用方法，Promise.race的作用，then方法里reject和catch的区别
promise的作用
  ● 解决多层嵌套 回调地狱
  ● 异步请求同步结果的问题
  
>Promise 常用三个场景。
>
处理异步回调
多个异步函数同步处理
异步依赖异步回调
封装统一的入口办法或者错误处理

#####Promise.race的作用
>race 如果有一个成功 就算是成功 （看谁跑的快 谁读的快就以谁为主）  Promise.race
返回的结果只是数组中的某一个
>Promise.race只要有一个promise对象进入 FulFilled 或者 Rejected 状态的话，就会继续进行后面的处理
注：promise.race在第一个函数执行完毕后，并不会取消其他函数的执行状态，但是其余函数执行完毕之后不会再调用.then

####区别
>使用.then即使 throwError 抛出了异常，onRejected 指定的函数也不会被调用。
使用.catch因为是链式操作，会捕获到上一步.then中抛出的操作

#####回调地狱 链式调用
>如果返回的是promise会调用promise的resolve  或者reject  如果成功了会放到下一个then的参数中
>如果返回的不是promise那then中的结果就是上一次的返回值 


----------


##工程化

####什么叫模块化？你用过哪些模块化解决方案？
>模块化更一种开发规范，比如cmd  amd 是为了更好的解藕，比如一个网站，按照不同的模块来开发，比如你有个评论区，a 项目有，b 项目有，如果仅是单纯的模块开发，这个js 文件你就可以单独来回引用，
更比如 ，一个页面 分好多个功能， 这时候你要是都写在一个js 中  会越来越大，
而你把他分成不同的模块，
比如评论是一块
分页又是一块，
已经上线，或你不做了，后期别人拉手，或你接手别人的项目，  这时候来个需求让你把分页去掉，或修改 你可以清楚的找到对应模块文件 进行修改 或去掉  
模块是自定义的，

####什么叫组件化？你在工作中是如何实现组件化的？
>组件，更想当于一个通用的东西，有的分功能组件，有的分业务组件
大图切换，这种就是单纯的一个效果展示，只要调用就ok 
一个分页，也是只单纯的调用，
组件更是一个多处都可以使用 ，不需要再单独开发的

####gulp和webpack的相同点和不同点?
>gulp
gulp强调的是前端开发的工作流程，我们可以通过配置一系列的task，定义task处理的事务（例如文件压缩合并、雪碧图、启动server、版本控制等），然后定义执行顺序，来让gulp执行这些task，从而构建项目的整个前端开发流程。
`PS：简单说就一个Task Runner`

>webpack
webpack是一个前端模块化方案，更侧重模块打包，我们可以把开发中的所有资源（图片、js文件、css文件等）都看成模块，通过loader（加载器）和plugins（插件）对资源进行处理，打包成符合生产环境部署的前端资源。
`PS：webpack is a module bundle`

###相同点
- 文件合并与压缩（css）
- 文件合并与压缩（js）
- sass/less预编译
- 启动server
- 版本控制

####不同点
>虽然都是前端自动化构建工具，但看他们的定位就知道不是对等的。
gulp严格上讲，模块化不是他强调的东西，他旨在规范前端开发流程。
webpack更是明显强调模块化开发，而那些文件压缩合并、预处理等功能，不过是他附带的功能。


####什么是热加载?
配置后可以不刷新浏览器 直接看到效果  
这样有个好处  很多开发用两个浏览器，这边改代码  另一边直接看效果了 很方便

##框架

####前端路由的实现原理
>路由（前端路由 后端路由）通过不同的路径返回不同的结果
  - 后端渲染   
  - 前后端分离  后端只提供接口  跳转逻辑由前端管理  速度会比以前快
  - spa 单页应用    优点：无刷新（不会每次都重新加载）切换的是页面中的组件  速度快
           但是首屏加载可能会导致速度变慢   （解决方法：首屏利用服务端渲染｜；路由切分）
           缺点：seo优化不能解决
  -  以前写代码都是多页开发-->缺点：体验效果，没有实现复用 每次都需要重新加载页面 
           例如：每个页面都要引jq

----------

####MVVM框架解决了什么问题？带来了什么问题？
- 数据驱动视图  视图也可以改变数据
>MVVM     model    view  viewModel
mvvm 模式只针对可以编辑可改变的元素 input  textarea


----------


####浏览器地址栏里面的'＃' 如何清楚？mode共有几个参数，参数有什么区别？



####vue中父组件如何给子组件传递值
>默认组件是独立 相互不能引用数据 可以通过属性的方式传递给儿子
(能在子组件中直接调用父组件中的数据，需要通过父组件的属性传递，
并且子组件要显示的通过props声明传递过来的属性)


----------


####react的优缺点
>优点
1、React速度很快：它并不直接对DOM进行操作，引入了一个叫做虚拟DOM的概念，安插在javascript逻辑和实际的DOM之间，性能好。
2、跨浏览器兼容：虚拟DOM帮助我们解决了跨浏览器问题，它为我们提供了标准化的API，甚至在IE8中都是没问题的。
3、一切都是component：代码更加模块化，重用代码更容易，可维护性高。
4、单向数据流：Flux是一个用于在JavaScript应用中创建单向数据层的架构，它随着React视图库的开发而被Facebook概念化。
5、同构、纯粹的javascript：因为搜索引擎的爬虫程序依赖的是服务端响应而不是JavaScript的执行，预渲染你的应用有助于搜索引擎优化。
6、兼容性好：比如使用RequireJS来加载和打包，而Browserify和Webpack适用于构建大型应用。它们使得那些艰难的任务不再让人望而生畏。


####React组件中props和state有什么区别？
-  state 是让组件控制自己的状态(state 的主要作用是用于组件保存、控制、修改自己的可变状态。)
-  props 是让外部对组件自己进行配置(props 的主要作用是让使用该组件的父组件可以传入参数来配置该组件)


----------


####什么是JSX
>JSX 是 JavaScript 语言的一种语法扩展，长得像 HTML，但并不是 HTML。
React.js 可以用 JSX 来描述你的组件长什么样的。
JSX 在编译的时候会变成相应的 JavaScript 对象描述。
react-dom 负责把这个用来描述 UI 信息的 JavaScript 对象变成 DOM 元素，并且渲染到页面上。


####说一下angular、vue、react的相同点和不同点?各适用于什么样的项目场景?
Angular/Vu与React有何本质区别?前者的设计思想是视图(view)绑定数据模型(model) 因此view可以直接修改model 后者的设计思想是视图 只是状态机的输出，因此view和store是解耦的 它们之间必须手动设置action和监听函数 才能建立联系

Vue.js的特性如下：
1.轻量级的框架
2.双向数据绑定
3.指令
4.插件化

>Vue.js与其他框架的区别？
1.与AngularJS的区别
相同点：
都支持指令：内置指令和自定义指令。
都支持过滤器：内置过滤器和自定义过滤器。
都支持双向数据绑定。
都不支持低端浏览器。
不同点：
1.AngularJS的学习成本高，比如增加了Dependency Injection特性，而Vue.js本身提供的API都比较简单、直观。
2.在性能上，AngularJS依赖对数据做脏检查，所以Watcher越多越慢。
Vue.js使用基于依赖追踪的观察并且使用异步队列更新。所有的数据都是独立触发的。
对于庞大的应用来说，这个优化差异还是比较明显的。

>2.与React的区别
相同点：
React采用特殊的JSX语法，Vue.js在组件开发中也推崇编写.vue特殊文件格式，对文件内容都有一些约定，两者都需要编译后使用。
中心思想相同：一切都是组件，组件实例之间可以嵌套。
都提供合理的钩子函数，可以让开发者定制化地去处理需求。
都不内置列数AJAX，Route等功能到核心包，而是以插件的方式加载。
在组件开发中都支持mixins的特性。
不同点：
React依赖Virtual DOM,而Vue.js使用的是DOM模板。React采用的Virtual DOM会对渲染出来的结果做脏检查。
Vue.js在模板中提供了指令，过滤器等，可以非常方便，快捷地操作DOM。


如果做应用系统，angular的生态环境已经成熟 yeoman bower gulp可以很快的把架子搭起来
如果做互联网前端，reactjs的模块化 + vdom + 搜索友好 可能就更合适 


----------


####React中不同组件传递数据的方式有哪些？至少说出三种
>1.（父组件）向（子组件）传递信息
2.（父组件）向更深层的（子组件） 进行传递信息  >>利用（context）
3.（子组件）向（父组件）传递信息
4.没有任何嵌套关系的组件之间传值（比如：兄弟组件之间传值）
5.利用react-redux进行组件之间的状态信息共享


####请描述React的组件加载生命周期函数以及shouldComponentUpdate方法的实际使用场景?
太长了
http://blog.csdn.net/slandove/article/details/50748473


----------


##HTTP

####HTTP报文的组成部分
```
http请求报文
请求行：http 2.0(http版本)    method(请求方式)  status 200 ok(状态码)
请求头：Accept 客户端可以接收的mime类型(区分消息内容类型)     mime类型：jpeg--->image/jpeg
请求体：在post请求体  用来传输数据  xhr.send(JSON.stringfiy(data))  
post请求通过请求体传输数据 get 是拼接查询字符串

http响应报文
响应行：http 2.0(http版本)     status 200 ok(状态码)
响应头：Connection:Keep-Alive     响应时间 Date: Tue, 22 Aug 2017 04:11:17 GMT
       告诉客户端 当前响应的内容  mime类型 字符编码格式  Content-Type:text/html;charset=utf-8   
响应体：响应的内容  通过response看
```

####GET和POST的区别
-  get    通常用来查询和获取  
- post  发送或更新（发送数据）

```
1、大小问题
输数据大小限制
get url  长度限制    
post     把数据放到请求体里 没有大小限制
（每个浏览器对于url的长度都存在限制，谷歌：8kb  火狐：7kb  IE：2kb  如果超过限制  并不会报错   
浏览器会把超出的部分截取）

2、缓存问题
get    缓存问题  解决：在 ？后面拼接个随机数或时间戳（拼接个时间）
post  是没有缓存的


3、安全问题 
get    将传递给后台的数据 拼接到url后面 容易被劫持  解决：MD5加密
post  是放在请求体里 传输过程中 看不到
```

####HTTP常见状态码
```

http status 状态码
  ● 200  201  202 都是请求成功
  ● 301  永久重定向/永久转移  eg:360buy   JD
  ● 302  临时重定向/临时转移
  ● 304  本次获取的内容是读取缓存中的数据（像npm下载 就是走的304）
  ● 400  401  402  4开头的都是客服端错误
  ● 400  参数出现错误（客户端传递给服务器端的参数）
  ● 401  无权限访问
  ● 404  客户端访问的地址不存在
  ● 500  未知的服务器错误
  ● 503  服务器 已经超负荷 
                   一台服务器能承受10000人，那么第10001人访问时，如果没有做“服务器的负载均衡”
                   那么这个人的状态码就是503
```

####什么是Restful API?
>1、Restful的意思就是表现层状态转化。
2、"表现层"其实指的是"资源"（Resources）的"表现层"，把"资源"具体呈现出来的形式，叫做它的"表现层"（Representation）。
3、所谓"资源"，就是网络上的一个实体，或者说是网络上的一个具体信息。它可以是一段文本、一张图片、一首歌曲、一种服务，总之就是一个具体的实在，每一个URI代表一种资源。
4、如果客户端想要操作服务器，必须通过某种手段，让服务器端发生"状态转化"（State Transfer）。而这种转化是建立在表现层之上的，所以就是"表现层状态转化"。
5、Restful就是客户端和服务器之间，传递这种资源的某种表现层
6、客户端通过四个HTTP动词，对服务器端资源进行操作，实现"表现层状态转化"
Restful API就是符合Restful架构的API设计。
>
Restful API一些具体实践：
1、应该尽量将API部署在专用域名之下。如果确定API很简单，不会有进一步扩展，可以考虑放在主域名下。
2、应该将API的版本号放入URL。
3、对于资源的具体操作类型，由HTTP动词表示
4、如果记录数量很多，服务器不可能都将它们返回给用户。API应该提供参数，过滤返回结果
5、如果状态码是4xx，就应该向用户返回出错信息。一般来说，返回的信息中将error作为键名


----------


####HTTPS和HTTP的区别是什么?
1、在URL前加https://前缀表明是用SSL加密的   电脑与服务器之间收发的信息传输将更加安全
2、Web服务器启用SSL需要获得一个服务器证书并将该证书与要使用SSL的服务器绑定。
3、http和https使用的是完全不同的连接方式,用的端口也不一样,前者是80,后者是443。http的连接很简单,是无状态的
4、HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议要比http协议安全

####从在浏览器中输入URL到页面渲染出来都经过了什么过程？
>输入地址
浏览器查找域名的 IP 地址
这一步包括 DNS 具体的查找过程，包括：浏览器缓存->系统缓存->路由器缓存...
浏览器向 web 服务器发送一个 HTTP 请求
服务器的永久重定向响应（从 http://example.com 到 http://www.example.com）
浏览器跟踪重定向地址
服务器处理请求
服务器返回一个 HTTP 响应
浏览器显示 HTML
浏览器发送请求获取嵌入在 HTML 中的资源（如图片、音频、视频、CSS、JS等等）
浏览器发送异步请求

####JSON和JSONP 区别是什么？JSONP的原理是？
```
JSONP原理
基本原理：利用script标签的异步加载特性实现
给服务端传一个回调函数，服务器返回一个传递过去的回调函数名称的JS代码
```

####用过那些跨域技术

####ajax的参数
```
$.ajax({    
        type: 'GET',    // 这是请求的方式 可以是GET方式也可以是POST方式, 默认是GET    
        url: ' xxx.php ',   // 这是请求的连接地址 一般情况下这个地址是后台给前端的一个连接，直接写就可以   
        dataType: 'json',  // 这是后台返回的数据类型 一般情况下都是一个json数据， 前端遍历一下就OK    
        async: true, // 默认为true，默认为true时，所有请求均为异步请求，如果需要发送同步请求，需设置为false,    
        timeout: 8000, // 设置请求超时时间（毫秒）。此设置将覆盖全局设置    
        data: {  
                // 要传递的参数  
                'xxx' : 'xxx',   
        },  
        beforeSend: function () {   
                // 在发送请求前就开始执行 （一般用来显示loading图）  
        }，    
        success: function (data) {    
                // 发送请求成功后开始执行，data是请求成功后，返回的数据  
        },    
        complete: function () {  
                //当请求完成后开始执行，无论成功或是失败都会执行 （一般用来隐藏loading图）            
        }，    
        error: function (xhr, textStatus, errorThrown) {  
                //  请求失败后就开始执行，请求超时后，在这里执行请求超时后要执行的函数   
        }  
}).done(function () {            
        // 这个函数是在ajax数据加载完之后，对数据进行的判断，在涉及到对ajax数据进行操作无效时，在这个函数里面写是可以起到效果的    
})  
```

----------


##前后端通信

####什么是同源策略及限制?
>同源策略（浏览器安全限制）
>1、同源 （三个只要有一个不一样就是跨域）  (都一样叫同源)
  ● 协议相同
  ● 域名相同
  ● 端口相同
>
2、限制
  ● cookie  localStorage 信息共享
  ● ajax 限制跨域  
    
什么是同源策略？
限制从一个源加载的文档或脚本如何与来自另一个源的资源进行交互。
一个源指的是主机名、协议和端口号的组合，必须相同

----------


####前后端如何通信?

####用原生JS模拟一下jquery的ajax方法

####跨域通信的几种方式?
- JSONP
- Hash
- postMessage
- WebSocket
- CORS

----------


##安全

####CSRF的原理以及如何防御
>CSRF：跨站请求伪造
其实就是网站中的一些提交行为，被黑客利用，在你访问黑客的网站的时候进行操作，会被操作到其他网站上
CSRF防御措施：
```
1、检测http referer是否是同域名
2、避免登录的session长时间存储在客户端中
3、关键请求使用验证码或者token机制
其他的一些攻击方法还有HTTP劫持、界面操作劫持
```


----------


####XSS的原生和如何防御
>XSS：跨站脚本攻击
它允许用户将恶意代码植入到提供给其他用户使用的页面中，可以简单的理解为一种javascript代码注入。
XSS的防御措施：
```
1、过滤转义输入输出
2、避免使用eval、new Function等执行字符串的方法，除非确定字符串和用户输入无关
3、使用cookie的httpOnly属性，加上了这个属性的cookie字段，js是无法进行读写的
4、使用innerHTML、document.write的时候，如果数据是用户输入的，那么需要对象关键字符进行过滤与转义
```
----------

##渲染机制

####什么是DOCTYPE及作用?标准模式和兼容模式有什么区别?

####浏览器是如何渲染页面的?

####什么是重排？什么时候会触发重排?
>  重排是更明显的一种改变，可以理解为渲染树需要重新计算
1. DOM元素的几何属性变化
2. DOM树的结构变化
3. 获取某些属性
 
####什么是重绘？什么时候会触发重绘?
>重绘是一个元素外观的改变所触发的浏览器行为
 1. 当html页面中部分局部样式 发生改变的时候（背景颜色  字体颜色）
 2. 浏览器只需要重新的渲染当前元素即可
 3. 重绘不会带来重新布局，并不一定伴随重排。

----------

##JS运行机制

####如何理解JS的单线程
>     因为JS运行在浏览器中，是单线程的，每个window一个JS线程，既然是单线程的，在某个特定的时刻只有特定的代码能够被执行，并阻塞其它的代码。而浏览器是事件驱动的（Event driven），浏览器中很多行为是异步（Asynchronized）的，会创建事件并放入执行队列中。javascript引擎是单线程处理它的任务队列，你可以理解成就是普通函数和回调函数构成的队列。当异步事件发生时，如mouse click, a timer firing, or an XMLHttpRequest completing（鼠标点击事件发生、定时器触发事件发生、XMLHttpRequest完成回调触发等），将他们放入执行队列，等待当前代码执行完成。

####什么是Event Loop,请简述其过程
  主线程从"任务队列"中读取事件，这个过程是循环不断的，所以整个的这种运行机制又称为Event Loop（事件循环）。
 主线程运行的时候，产生堆（heap）和栈（stack），栈中的代码调用各种外部API，它们在"任务队列"中加入各种事件（click，load，done）。只要栈中的代码执行完毕，主线程就会去读取"任务队列"，依次执行那些事件所对应的回调函数。执行栈中的代码（同步任务），总是在读取"任务队列"（异步任务）之前执行。


----------
##服务器

####如何在web应用中在实现权限控制?

####Web服务器、应用服务器、Web容器、反向代理服务器的区别和联系?


----------
##错误处理

####前端错误的分类?
- 即时运行错误（代码错误）
- 资源加载错误
- 
####程序出现bug了，你是如何调试的?
然后alert或console.log

####如何分类捕获不同的错误?
即时运行错误的捕获方式：
1、try...catch
2、window.onerror

资源加载错误：
1、object.onerror（如img,script）
2、performance.getEntries()
3、Error事件捕获

####如何把生产环境的错误上报？
- 采用Ajax通信方式上报
- 利用Image对象上报

----------
##页面性能

####前端性能优化的方法有哪些？至少说出10种以上
>第一：面向内容的优化
1. 减少 HTTP 请求 
2. 减少 DNS 查找
3. 避免重定向
4. 使用 Ajax 缓存
5. 延迟载入组件
6. 预先载入组件 
7. 减少 DOM 元素数量
8. 切分组件到多个域
9. 最小化 iframe 的数量
10.  不要出现http 404 错误
第二：面向 Server
1. 缩小 Cookie 
2. 针对 Web 组件使用域名无关性的

- 减少Dom操作
- 压缩JS和CSS
- HTML等
- DNS预解析
- 雪碧图
- 移动端响应式图片
- 静态资源CDN

----------

####如何实现JS的异步加载? async和defer的区别是什么?
>   defer是在HTML解析完之后才会执行，如果是多个，按照加载的顺序依次执行    
     async是在加载完成后立即执行，如果是多个，执行顺序和加载顺序无关

----------
##缓存

####Expires和Cache-Control是如何工作的？
####Last-Modified和Etag是如何工作的？
####请描述cookie、sessionStorage和localStorage的区别

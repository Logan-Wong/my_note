## Front-end 面试题（非算法）

> **个人对面试的理解和心得：**要记住在面试时，我们和面试官是平等的，而且面试官也非常欣赏喜欢交谈的人，在面试的时候能够去表达自己的想法，往往会给面试官留下非常好的印象。

> 回答问题大体思路：
>
> 1. 突出自己项目经验较丰富
> 2. 平时关注技术时事，新老技术对比区别
> 3. 平时会自学进步
>
> 举例（多方案问题）：这种需求在我之前的项目当中的非常常见的，刚开始的话我只用了方案 A，后来呢随着某某技术的兴起，方案 B 用起来也特别方便、强大，有一段时间我自己看掘金、博客的时候，发现方案 C 也可以实现这种需求，感觉挺好玩的，所以我就记下来了。

### 1 HTML

#### 1.1 HTML5 新增内容

HTML5 有更大的技术集，允许构建更多样化和更强大的网站和应用程序。这个集合有时称为HTML5和它的朋友们，不过大多数时候仅缩写为一个词 **HTML5**。

##### 语义

##### 通信

##### 离线存储

##### 多媒体

##### 2D / 3D 绘图效果

##### 性能集成

##### 设备访问

##### 样式设计



##### 结构标签

- header：头部标签。定义页面或章节的头部。它经常包含 logo、页面标题和导航性的目录；
- nav：导航标签。定义只包含导航链接的章节；

- article：内容标签。定义页面中一块与上下文不相关的独立内容，比如博客中的一篇文章；
- section：块级标签。定义文档中的一个章节；
- aside：侧边栏标签。定义和页面内容关联度较低的内容——如果被删除，剩下的内容仍然很合理；
- footer：尾部标签。定义页面或章节的尾部。它经常包含版权信息、法律信息链接和反馈建议用的地址；
- hgroup：定义文件中一个区块的相关信息；
- figure：代表一个和文档有关的图例。

##### 多媒体标签（嵌入内容）

- video：代表一段视频及其视频文件和字幕，并提供了播放视频的用户界面；
- audio：代表一段声音，或音频流；
- source：为 `<video>` 或 `<audio>` 这类媒体元素指定媒体源；
- embed：代表一个嵌入的外部资源，如应用程序或交互内容；
- canvas：代表位图区域，可以通过脚本在它上面实时呈现图形，如图表、游戏绘图等。

##### 其他标签

- ruby：代表被 ruby 注释标记的文本，如中文汉字和它的拼音；
- rp：代表 ruby 注释两边的额外插入文本，用于在不支持 ruby 注释显示的浏览器中提供友好的注释显示；
- rt：代表 ruby 注释，如中文拼音；
- mark：代表一段需要被高亮的引用文字；
- datalist：代表提供给其他控件的一组预定义选项；
- output：代表一个 `<select>` 元素或 `<datalist>` 元素中的一个选项；
- keygen：代表一个密钥对生成器控件；
- time：代表日期和时间值，机器可读的等价形式通过 datetime 属性指定。

##### input 的 type

- email：限制为 Email 类型；
- url：限制为 URL 类型；
- date：限制为日期类型；
- time：限制为时间类型；
- month：限制为月份；
- week：限制为周；
- number：限制为数字类型；
- tel：限制为手机号码；
- search：限制为搜索框；
- color：生成一个颜色选择表单。

##### 表单属性

- required：内容不能为空，必填；
- placeholder：提供文本（占位符），表单的提示信息；
- autofocus：自动聚焦属性；
- autocomplete：off / on，默认打开，记录之前键入过的值；
- multiple：可以多选文件提交。

---

### 2 CSS

#### 2.1 你怎么理解盒子模型？

解答思路：

盒子模型有两种，W3C（标准） 和 IE 盒子模型；

1. W3C 定义的盒子模型包括 margin、border、padding、content ，元素的 width / height = content 的宽度 / 高度；

    ![img](https://gitee.com/wlogan/pic-go-picture-bed/raw/master/images/20200907203812.bmp)

2. IE 盒子模型与 W3C 的盒子模型唯一区别就是元素的宽度，元素的 width / height = content + padding + border；

    ![img](https://gitee.com/wlogan/pic-go-picture-bed/raw/master/images/20200907204343.bmp)

**示范回答：**

我认为 W3C 定义的盒子模型与 IE 定义的盒子模型相比较，IE 定义的比较合理，元素的宽度应该包含 border（边框）和 padding（填充），这个和我们现实生活的盒子是一样的，W3C 也认识到自己的问题了，所以在 CSS3 中新增了一个样式 box-sizing，包含两个属性 content-box 和 border-box。

1. **content-box（默认值）：**元素的 width = content + padding + border；

    ```css
    .test1{
    	box-sizing:content-box;
    	width:200px;
    	padding:10px;
    	border:15px solid #eee;
    }
    ```

    ![image-20200907205232263](https://gitee.com/wlogan/pic-go-picture-bed/raw/master/images/20200907205232.png)

2. **border-box：**元素的 width = width（相当于缩小 content 的宽度）

    ```css
    .test1{
    	box-sizing:border-box;
    	width:200px;
    	padding:10px;
    	border:15px solid #eee;
    }
    ```

    ![img](https://gitee.com/wlogan/pic-go-picture-bed/raw/master/images/20200907205216.png)

**值得注意的是：**普通文档流的块元素，会有外边距合并的问题，其大小为两值中的最大值，而浮动和绝对定位则不会。

#### 2.2 flex 布局

![flex布局](https://gitee.com/wlogan/pic-go-picture-bed/raw/master/images/20200907140533.png)

#### 2.3 用 CSS3 写一个一直顺时针旋转的 loading 动画

思路：先给 div 长和宽，边框，变圆，然后将三条边透明，让这个 div 一直旋转即可

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="loaders.css" type="text/css">
    <style>
        #container {
          margin-left:30px;
          font-size: 12px;
          color: #c0c0c0;
          display: flex;
          flex-wrap: wrap;
          width: 700px;
          background-color: #17607D;
          padding-top:20px;
        }
        .vbox{
          display: flex;
          flex-direction: column;
          align-items: center;
          width:140px;
          height:140px;
        }
        .vbox > div{
          margin-top: 30px;
        }
        // 定义动画
        @keyframes rotate {
            0% {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
            50% {
                -webkit-transform: rotate(180deg);
                transform: rotate(180deg);
            }
            100% {
                -webkit-transform: rotate(360deg);
                transform: rotate(360deg);
            }
		}
        .ball-clip-rotate > div {
            background-color: #fff;
            width: 15px;
            height: 15px;
            border-radius: 100%;
            margin: 2px;
            -webkit-animation-fill-mode: both;
            animation-fill-mode: both;
            border: 2px solid #fff;
            border-bottom-color: transparent;
            border-right-color: transparent;
            border-left-color: transparent;
            height: 26px;
            width: 26px;
            background: transparent !important;
            display: inline-block;
            -webkit-animation: rotate 0.75s 0s linear infinite;
            animation: rotate 0.75s 0s linear infinite;
        }
      </style>
</head>
<body>
    <div id="container">
        <div class="vbox">
            ball-clip-rotate
            <div class="ball-clip-rotate">
            	<div></div>
            </div>
        </div>
    </div>
</body>
</html>
```

#### 2.4 CSS 三大特性

1. 层叠性

2. 继承性

    以 text-、font-、line- 开头的以及 color 属性都可以继承

3. 优先级

#### 2.5 说一说 CSS 的选择器的优先级

| 标签选择器             | 计算权重公式 |
| ---------------------- | ------------ |
| 继承或者 *             | 0,0,0,0      |
| 每个元素（标签选择器） | 0,0,0,1      |
| 每个类，伪类           | 0,0,1,0      |
| 每个ID                 | 0,1,0,0      |
| 每个行内样式 style=""  | 1,0,0,0      |
| 每个!important  重要的 | ∞ 无穷大     |

值从左到右，左面的最大，一级大于一级，数位之间没有进制，级别之间不可超越。

- div ul  li   ------>     0,0,0,3
- .nav ul li  ------>     0,0,1,2
- a:hover   -----—>   0,0,1,1
- .nav a      ------>      0,0,1,1

#### 2.6 说一说盒子的水平垂直居中

- 定位（3 种）

    1. 父盒子相对定位，子盒子绝对定位移动上左各 50%，然后再反向移动自身一半的宽高（需要知道子盒子的宽高）；

        ```html
         <!DOCTYPE html>
         <html lang="en">
         <head>
             <meta charset="UTF-8">
             <meta name="viewport" content="width=device-width, initial-scale=1.0">
             <title>Document</title>
             <style>
                .container {
                    position: relative;
                    width: 500px;
                    height: 500px;
                    background-color: pink;
                }
                .box {
                    position: absolute;
                    top: 50%;
                    left: 50%;
                    margin-top: -50px;
                    margin-left: -50px;
                    width: 100px;
                    height: 100px;
                    background-color: lightblue;
                }
             </style>
         </head>
         <body>
            <div class="container">
                <div class="box"></div>
              </div>
         </body>
         </html>
        ```

    2. 父盒子相对定位，子盒子绝对定位移动上左各 50%，然后再反向移动自身一半的宽高（不需要知道子盒子的宽高）

        ```html
         <!DOCTYPE html>
         <html lang="en">
         <head>
             <meta charset="UTF-8">
             <meta name="viewport" content="width=device-width, initial-scale=1.0">
             <title>Document</title>
             <style>
                .container {
                    position: relative;
                    width: 500px;
                    height: 500px;
                    background-color: pink;
                }
                .box {
                    position: absolute;
                    top: 50%;
                    left: 50%;
                    transform: translate(-50%, -50%);
                    width: 100px;
                    height: 100px;
                    background-color: lightblue;
                }
             </style>
         </head>
         <body>
            <div class="container">
                <div class="box"></div>
              </div>
         </body>
         </html>
        ```

    3. 父盒子相对定位，子盒子绝对定位，但不移动，给子盒子 margin: auto;

        ```html
         <!DOCTYPE html>
         <html lang="en">
         <head>
             <meta charset="UTF-8">
             <meta name="viewport" content="width=device-width, initial-scale=1.0">
             <title>Document</title>
             <style>
                .container {
                    position: relative;
                    width: 500px;
                    height: 500px;
                    background-color: pink;
                }
                .box {
                    position: absolute;
                    top: 0;
                    bottom: 0;
                    left: 0;
                    right: 0;
                    margin: auto;
                    width: 100px;
                    height: 100px;
                    background-color: lightblue;
                }
             </style>
         </head>
         <body>
            <div class="container">
                <div class="box"></div>
              </div>
         </body>
         </html>
        ```

- display：flex 父盒子用 flex 布局，设置主轴和侧轴元素 center

    ```html
     <!DOCTYPE html>
     <html lang="en">
     <head>
         <meta charset="UTF-8">
         <meta name="viewport" content="width=device-width, initial-scale=1.0">
         <title>Document</title>
         <style>
            .container {
                display: flex;
                justify-content: center;
                align-items: center;
                width: 500px;
                height: 500px;
                background-color: pink;
            }
            .box {
                width: 100px;
                height: 100px;
                background-color: lightblue;
            }
         </style>
     </head>
     <body>
        <div class="container">
            <div class="box"></div>
          </div>
     </body>
     </html>
    ```

- js 本质上也是用定位，让子盒子偏移（父盒子宽度 - 子盒子宽度）/ 2 的距离

    ```javascript
    let container = document.querySelector('.container'),
        box = document.querySelector('.box'),
        conW = container.clientWidth,
        conH = container.clientHeight,
        boxW = box.clientWidth,
        boxH = box.clientHeight
    container.style.position = 'relative'
    box.style.position = 'absolute'
    box.style.left = (conW - boxW) / 2 + 'px'
    box.style.top = (conH - boxH) / 2 + 'px'
    ```


#### 2.7 你知道 BFC 吗

BFC(Block formatting context)直译为"块级格式化上下文"。BFC 可以看作元素的一种属性，当元素拥有了 BFC 这个属性的时候，它就可以看作是隔离了的独立容器，容器里面的元素不会在布局上影响到外面的元素。

触发条件：

- 根元素，即 HTML 元素
- float 的值不为 none
- overflow 的值不为 visible
- display 的值为 inline-block、table-cell（表格单元格）、table-caption（表格标题）、table、table-row、table-row-group、table-header-group、table-footer-group 和 inline-table
- position 的值为 absolute、fixed

作用：

- 避免外边距重叠
- 清除浮动
- 阻止元素被浮动元素覆盖（自适应两栏布局？？？）

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    .container {
      width: 500px;
      height: 200px;
      background-color: pink;
    }
    .boxLeft {
      float: left;
      width: 100px;
      height: 150px;
      background-color: lightblue;
    }
    .boxright {
      /* 触发 BFC */
      overflow: auto;
      /* 不能给宽，也不能是 100% */
      height: 200px;
      background-color: purple;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="boxLeft">1</div>
    <div class="boxright">2</div>
  </div>
</body>
</html>
```

#### 2.8 谈一谈你对 CSS modules 的理解，以及跟 CSS scoped 的差异

#### 2.9 使用 CSS，让一个 dⅳ 消失在视野中，发挥想象力？

#### 2.10 实现左右固定，中间自适应布局方案有哪些

- 圣杯布局：浮动、padding 和负 margin

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>圣杯布局</title>
        <style>
            .header {
    			width: 100%;
    			height: 100px;
    			background: lightblue;
    		}
    
    		.content {
                /* 触发 BFC */
    			overflow: hidden;
    			padding: 0 200px;
    		}
    
    		.footer {
    			width: 100%;
    			height: 100px;
    			background: lightblue;
    		}
    
    		.middle {
    			float: left;
    			/* position: relative; */
    			width: 100%;
    			height: 500px;
    			background: pink;
    		}
    		.left {
    			float: left;
    			position: relative;
    			left: -200px;
    			width: 200px;
    			height: 500px;
    			margin-left: -100%;
    			background: yellow;
    		}
    		.right {
    			float: left;
    			position: relative;
    			right: -200px;
    			width: 200px;
    			height: 500px;
    			margin-left: -200px;
    			background: green;
    		}
        </style>
    </head>
    <body>
        <div class="header">头头</div>
        <div class="content">
    		<div class="middle">123</div>
    		<div class="left">456</div>
    		<div class="right">789</div>
    	</div>
    	<div class="footer">尾尾</div>
    </body>
    </html>
    ```

- 双飞翼布局：浮动、margin 和 -margin

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>双飞翼布局</title>
        <style>
            .header {
    			width: 100%;
    			height: 100px;
    			background: lightblue;
    		}
    
    		.content {
                /* 触发 BFC */
    			overflow: hidden;
    		}
    
    		.footer {
    			width: 100%;
    			height: 100px;
    			background: lightblue;
    		}
    
    		.middle {
    			float: left;
    			width: 100%;
                /* padding: 0 200px; */
    		}
            .inner-middle {
    			/* width: auto; */
    			height: 500px;
                margin: 0 200px;
    			background: pink;
    		}
            
    		.left {
    			float: left;
    			width: 200px;
    			height: 500px;
    			margin-left: -100%;
    			background: yellow;
    		}
    		.right {
    			float: left;
    			width: 200px;
    			height: 500px;
    			margin-left: -200px;
    			background: green;
    		}
        </style>
    </head>
    <body>
        <!-- 双飞翼布局 -->
        <div class="header">头头</div>
    	<div class="content">
    		<div class="middle">
    			<div class="inner-middle">123</div>
    		</div>
    		<div class="left">456</div>
    		<div class="right">789</div>
    	</div>
    	<div class="footer">尾尾</div>
    </body>
    </html>
    ```

- flex

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>flex 实现左右固定，中间自适应布局</title>
        <style>
            .header {
    			width: 100%;
    			height: 100px;
    			background: lightblue;
    		}
    
    		.content {
                display: flex;
                /* 容器内的 item，两边贴边，中间平分空间 */
                justify-content: space-between;
    		}
    
    		.footer {
    			width: 100%;
    			height: 100px;
    			background: lightblue;
    		}
    
    		.left {
                /* 不放大不缩小，固定该 item 主轴空间为 200px */
                flex: 0 0 200px;
    			height: 500px;
    			background: yellow;
    		}
    		.middle {
                /* 考虑到该容器中其他 item flex-grow 属性值都为 0，而这里为 1，所以该 item 会占据所有主轴剩余空间 */
                flex: 1;
    			height: 500px;
    			background: pink;
    		}
    		.right {
                flex: 0 0 200px;
    			height: 500px;
    			background: green;
    		}
        </style>
    </head>
    <body>
        <div class="header">头头</div>
        <div class="content">
            <div class="left">456</div>
    		<div class="middle">123</div>
    		<div class="right">789</div>
    	</div>
    	<div class="footer">尾尾</div>
    </body>
    </html>
    ```

- 定位

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>定位实现左右固定，中间自适应布局</title>
        <style>
            .header {
    			width: 100%;
    			height: 100px;
    			background: lightblue;
    		}
    
    		.content {
                position: relative;
    		}
    
    		.footer {
    			width: 100%;
    			height: 100px;
    			background: lightblue;
    		}
    
    		.left {
                position: absolute;
                top: 0;
                left: 0;
                width: 200px;
    			height: 500px;
    			background: yellow;
    		}
    		.middle {
                margin: 0 200px;
    			height: 500px;
    			background: pink;
    		}
            .right {
                position: absolute;
                top: 0;
                right: 0;
                width: 200px;
    			height: 500px;
    			background: green;
    		}
        </style>
    </head>
    <body>
        <div class="header">头头</div>
        <div class="content">
            <div class="left">456</div>
    		<div class="middle">123</div>
    		<div class="right">789</div>
    	</div>
    	<div class="footer">尾尾</div>
    </body>
    </html>
    ```

    

---

### 3 JavaScript

#### 3.1 构造函数实例和原型对象三角关系

- 构造函数的 prototype 属性指向了构造函数原型对象
- 实例对象是由构造函数创建的,实例对象的 \__proto__ 属性指向了构造函数的原型对象
- 构造函数的原型对象的 constructor 属性指向了构造函数,实例对象的原型的 constructor 属性也指向了构造函数

![img4](https://gitee.com/wlogan/pic-go-picture-bed/raw/master/images/20200907140552.png)

#### 3.2 原型链

每一个实例对象又有一个 \_\_proto\_\_ 属性，指向的构造函数的原型对象，构造函数的原型对象也是一个对象，也有 \__proto__ 属性，这样一层一层往上找就形成了原型链。

![img5](https://gitee.com/wlogan/pic-go-picture-bed/raw/master/images/20200907140602.png)

#### 3.3 数组去重

1. 通过ES6新特性 Set() 实现

    如：

    ```javascript
    var arr = [1, 2, 3, 1, 2]
    var newArr = [...new Set(arr)]
    ```

    

2. 自己封装函数实现

    思路：定义一个新对象和新数组，将传入数组中的每个元素都作为新对象的 key，将其 value 改为 true（表示数组中有该元素），同时将该元素 push 到新数组，这样遍历完传进来的数组，新数组中便能得到去重的数组

    ```javascript
    function uniqueArray(arr) {
    	if (!arr instanceof Array) {
            throw Error('当前传入的不是数组')
        }
        let newArr []
        let obj = {}
        arr.forEach(item => {
            if (!obj[item]) {
                newArr.push(item)
                obj[item] = true
            }
        })
        return newArr
    }
    ```



#### 3.4 请介绍一下 this

大多数情况，this 总是指向调用该函数的对象！

- 常规函数：谁调用该函数，this就指向该调用者，全局环境下调用函数执行，this 指向 window
- 箭头函数：
    - 箭头函数不绑定 this，相当于普通变量；
    - 箭头函数的 this 寻值行为与普通变量相同，在作用域中逐级寻找；

![img1](https://gitee.com/wlogan/pic-go-picture-bed/raw/master/images/20200907140741.png)

有如下方法改变函数内部 this 指向：

1. **call 方法**

    call() 方法调用一个**对象**。简单理解为调用函数的方式，但是它可以改变函数的 this 指向

    ```javascript
var o = {
    	name: 'andy'
    }
    function fn(a, b) {
    	console.log(this)
        console.log(a + b)
    };
    fn(1,2)			// 此时的 this 指向的是 window，运行结果为3
    fn.call(o,1,2)	// 此时的 this 指向的是对象 o,参数使用逗号隔开,运行结果为3
    ```
    
    **应用场景:**  经常做继承

    ```javascript
 // 1. 父构造函数
     function Father(uname, age) {
       // this 指向父构造函数的对象实例
       this.uname = uname;
       this.age = age;
     }
    // 2 .子构造函数 
    function Son(uname, age, score) {
      // this 指向子构造函数的对象实例
      // 3.使用 call 方式实现子继承父的属性
      Father.call(this, uname, age);
      this.score = score;
    }
    var son = new Son('刘德华', 18, 100);
    console.log(son);
    ```
    
2. **apply 方法**

    apply() 方法调用一个**函数**。简单理解为调用函数的方式，但是它可以改变函数的 this 指向。

    ```javascript
    var o = {
    	name: 'andy'
    }
    function fn(a, b) {
     	console.log(this)
        console.log(a + b)
    };
    fn()				// 此时的 this 指向的是 window，运行结果为3
    fn.apply(o,[1,2])	// 此时的 this 指向的是对象 o,参数使用数组传递，运行结果为3
    ```

    应用场景:  经常跟数组有关系，比如利用 Math.max 求数组元素的最大值（数组中没有直接求最大值的方法）

    ```javascript
    var arr = [1, 66, 3, 99, 4]
    var max = Math.max.apply(Math, arr)
    var min = Math.min.apply(Math, arr)
    console.log(max, min)
    ```

3. **bind 方法**

    bind() 方法不会调用函数，但是能改变函数内部 this 指向，返回的是原函数改变 this 之后产生的新函数

    如果只是想改变 this 指向，并且不想调用这个函数的时候，可以使用 bind

    ```javascript
    var o = {
     	name: 'andy'
    };
    
    function fn(a, b) {
    	console.log(this);
    	console.log(a + b);
    };
    var f = fn.bind(o, 1, 2); 	// 此处的 f 是 bind 返回的新函数
    f();						// 调用新函数 this 指向的是对象 o，参数使用逗号隔开
    ```

    应用场景：不调用函数，但是还想改变 this 指向

    ```javascript
    // 有一个按钮，当我们点击了之后，就禁用该按钮，三秒之后再自动激活
    var btn = document.querySelector('button')
    btn.onclick = function() {
        this.disabled = true
        setTimeout(function() {
            this.disabled = false	// 此时 this 指向 btn
        }.bind(this), 3000)
    }
    ```


call、apply、bind三者的异同

- 共同点：都可以改变 this 指向
- 不同点：
    - call 和 apply  会调用函数，而 bind  不会
    - call 和 apply 传递的参数不一样，call 传递参数使用逗号隔开，apply 使用数组传递


- 应用场景
    1. call 经常做继承
    2. apply 经常跟数组有关系。比如借助于数学对象实现数组最大值最小值
    3. bind 不调用函数，但是可以改变this指向。比如改变定时器内部的 this 指向

实例一：

```javascript
function foo() { 
    console.log(this.bar); 
} 
var bar = "bar1"; 
var o2 = {bar: "bar2", foo: foo}; 
var o3 = {bar: "bar3", foo: foo}; 

foo();			// 预期输出 "bar1" - 默认绑定
o2.foo();       // 预期输出 "bar2" - 隐式绑定
foo.call(o3);	// 预期输出 "bar3" - 显示绑定，使用对象作为 this
```

**解析：**通过 call、apply、bind 调用的函数，都是显示绑定

实例二：

```javascript
var name = 'Nicolas';
function Person() {
    this.name = 'Smiley';
    this.sayName = function() {
        console.log(this); 
        console.log(this.name); 
    };
    setTimeout(this.sayName, 0);     // 预期输出 window，Nicolas
}

var person = new Person();	// 关键字 new 绑定
person.sayName();			// 预期输出 Person，Smiley
```

**解析：**如果在函数调用前面加上 new，那么这个函数中的 this 就是这个新的对象。

实例三：

```javascript
function Person() {
  	this.name = "Smiley";
  	this.sayName = function() {
    	console.log(this);
    	console.log(this.name); 
  	};
}

let person = new Person();
person.sayName.call({name: "Nicolas"});		// 预期输出 {name: "Nicolas"}，"Nicolas"
```

**解析：**显示绑定，其 this 指向 call 中第一个参数，也即是对象 {name: "Nicolas"}

实例四：

```javascript
function Person() {
  	this.name = "Smiley";
  	this.sayName = function() {
    	console.log(this);
    	console.log(this.name); 
  	};
}

let person = new Person();
let sayNameCopy = person.sayName;
sayNameCopy();	// 预期输出 window，undefined
```

**解析：**符合默认绑定的规则

实例五：

```javascript
function Person() {
  	this.name = "Smiley";
  	this.sayName = ()=> {
    	console.log(this);
    	console.log(this.name); 
  	};
}

let person = new Person();
person.sayName.call({name: "Nicolas"});		// 预期输出 Person，"Smiley"
```

**解析：**箭头函数并没有自己的 this，被定义在哪里，this 就指向谁，且优先级比显式调用高，因此，this 指向Person

#### 3.5 封装深拷贝（递归）

```javascript
function deepCopy(newObj, oldObj) {
    for (var k in oldObj) {
        var item = oldObj[k]
        // 判断属性值属于哪种类型
        if (item instanceof Array) {
            newObj[k] = []
            deepCopy(newObj[k], item)
        } else if (item instanceof Object) {
            newObj[k] = {}
            deepCopy(newObj[k], item)
        } else {
            newObj[k] = item
        }
    }
}
```

#### 3.6 js 中的数据类型（9种）（含ES6）

在JavaScript中，除了5种原始数据类型之外，其他所有的都是对象，包括函数（Function）。

**基本数据类型：**String，Boolean，Number，Undefined，Null，BigInt，Symbol

**引用数据类型：**Object（Array，Date，RegExp，Function）

#### 3.7 js 实现继承的方式

常见的共有 5 种，如下：

- 类式继承

    ```javascript
    // 声明父类
    function Animal() {
      	this.name = 'animal';
      	this.type = ['pig', 'cat'];
    }
    
    // 为父类添加共有方法
    Animal.prototype.greet = function(sound) {
      	console.log(sound);
    }
    
    // 声明子类
    function Dog() {
      	this.name = 'dog';
    }
    
    // 继承父类
    Dog.prototype = new Animal();
    
    var dog = new Dog();
    dog.greet('汪汪');		//  "汪汪"
    console.log(dog.type);	// ["pig", "cat"]
    ```

    **原理：**在实例化一个类时，新创建的对象复制了父类的构造函数内的属性与方法并且将原型 _proto__ 指向了父类的原型对象，这样就拥有了父类的原型对象上的属性与方法。

    缺点：

    - 引用缺陷：

        ```javascript
        dog.type.push('dog');
        var dog2 = new Dog();
        console.log(dog2.type);  // ["dog", "cat", "dog"]
        ```

        当通过 dog 实例对象修改继承自 Animal 中的数组 type (引用类型)时，另外一个新创建的实例 dog2 也会受到影响。

    - 无法为不同的实例初始化继承来的属性（子类型创建时不能向父类型传递参数？）：

        ```javascript
        function Animal(color) {
          	this.color = color;
        }
        ...
        Dog.prototype = new Animal('白色');
        ...
        console.log(dog.color); // "白色"
        console.log(do2.color); // "白色"
        ```
    
- 构造函数继承

    ```javascript
    // 声明父类
    function Animal(color) {
      	this.name = 'animal';
      	this.type = ['pig','cat'];
      	this.color = color;
    }
    
    // 添加共有方法
    Animal.prototype.greet = function(sound) {
      	console.log(sound);
    }
    
    // 声明子类
    function Dog(color) {
      	Animal.call(this, color);	// 改变 Animal 父类 this 指向子类
    }
    
    var dog = new Dog('白色');
    var dog2 = new Dog('黑色');
    
    dog.type.push('dog');
    console.log(dog.color);  	// "白色"
    console.log(dog.type);  	// ["pig", "cat", "dog"]
    
    console.log(dog2.type);  	// ["pig", "cat"]
    console.log(dog2.color);  	// "黑色"
    ```

    缺点：

    - 无法获取到父类的共有方法，也就是通过原型 prototype 绑定的方法：

        ```javascript
        dog.greet();  // Uncaught TypeError: dog.greet is not a function
        ```

- 组合继承

    ```javascript
    // 声明父类   
    function Animal(color) {    
        this.name = 'animal';    
        this.type = ['pig','cat'];    
        this.color = color;   
    }     
    
    // 添加共有方法  
    Animal.prototype.greet = function(sound) {    
      	console.log(sound);   
    }     
    
    // 声明子类   
    function Dog(color) { 
        // 构造函数继承    
        Animal.call(this, color);   // 继承实例属性，第一次调用 Animal()
    }   
    
    // 类式继承
    Dog.prototype = new Animal();   	// 继承父类方法，第二次调用 Animal()
    
    var dog = new Dog('白色');   
    var dog2 = new Dog('黑色');     
    
    dog.type.push('dog');   
    console.log(dog.color); // "白色"
    console.log(dog.type);  // ["pig", "cat", "dog"]
    
    console.log(dog2.type); // ["pig", "cat"]
    console.log(dog2.color);  // "黑色"
    dog.greet('汪汪');  // "汪汪"
    ```

    组合继承综合了类式继承和构造函数继承的优点，同时去除了缺陷。

    但有新的小缺陷，那就是它调用了 2 次父类的构造函数！

- 寄生组合式继承

    ```javascript
    function Animal(color) {
        this.color = color;
        this.name = 'animal';
        this.type = ['pig', 'cat'];
    }
    
    Animal.prototype.greet = function(sound) {
      	console.log(sound);
    }
    
    function Dog(color) {
        Animal.call(this, color);
        this.name = 'dog';
    }
    
    /* 注意下面两行 */
    Dog.prototype = Object.create(Animal.prototype);
    Dog.prototype.constructor = Dog;
    
    Dog.prototype.getName = function() {
      	console.log(this.name);
    }
    
    var dog = new Dog('白色');   
    var dog2 = new Dog('黑色');     
    
    dog.type.push('dog');   
    console.log(dog.color);   	// "白色"
    console.log(dog.type);   	// ["pig", "cat", "dog"]
    
    console.log(dog2.type);  	// ["pig", "cat"]
    console.log(dog2.color);  	// "黑色"
    dog.greet('汪汪');		   // "汪汪"
    ```

    在上面的例子中，我们并不像构造函数继承一样直接将父类 Animal 的一个实例赋值给 Dog.prototype，而是使用 Object.create( ) 进行一次浅拷贝，将父类原型上的方法拷贝后赋给 Dog.prototype，这样子类上就能拥有了父类的共有方法，而且少了一次调用父类的构造函数。

    这里还需注意一点，由于对Animal的原型进行了拷贝后赋给 Dog.prototype，因此 Dog.prototype 上的constructor 属性也被重写了，所以我们通过 Dog.prototype.constructor = Dog 修复。

- extends 继承

    Class 和 extends 是在 ES6 中新增的，Class 用来创建一个类，extends 用来实现继承：

    ```javascript
    class Animal {   
        constructor(color) {   
            this.color = color;   
        }   
        greet(sound) {   
            console.log(sound);   
        }  
    }   
    
    class Dog extends Animal {   
        constructor(color) {   
            super(color);   
            this.color = color;   
        }  
    }   
    
    let dog = new Dog('黑色');  
    dog.greet('汪汪');		// "汪汪"
    console.log(dog.color);	// "黑色"
    ```

#### 3.8 为什么 0.1 + 0.2 !== 0.3 ？如何解决？

0.1 + 0.2 = 0.30000000000000004

> 在 JS 中的 Number 类型，二进制小数的有效位数只有 52 位，从 0到 51 位（包括边界）

#### 3.9 onchange、oninput 和 onpropertychange的区别

- onpropertychange IE 专属；
- oninput 兼容 IE9 及以上；
- oninput 和 onpropertychange 实时触发，onchange 在元素失去焦点时触发；
- 通过 js 改变 value 不会触发 oninput，但 onpropertychange 会。

#### 3.10 new 出构造函数会执行哪些操作

1. 在内存中创建一个新对象；
2. 新对象内部的 [[Prototype]] 特性被赋值为构造函数的 prototype 属性；
3. this 指向新对象；
4. 给新对象添加属性；
5. 返回刚创建的新对象。

#### 3.11 比较运算

##### == 数据类型不一样时

- 对象 == 字符串，对象.toString() 变为字符串
- null == undefined，但是和其他值比较就不再相等了
- NaN == NaN，不相等，和其他值比较更不可能相等
- 剩下的都是转换为数字

---

### 4 ES6 新特性

#### 4.1 let 关键字

```javascript
var arr = [];
 for (var i = 0; i < 2; i++) {
     arr[i] = function () {
         console.log(i); 
     }
 }
 arr[0]();	// 预期输出 2
 arr[1]();	// 预期输出 2
```

图解：关键点在于变量 i 是全局的，函数执行时输出的都是全局作用域下的 i 值

![let面试题](https://gitee.com/wlogan/pic-go-picture-bed/raw/master/images/20200907140614.png)

```javascript
 let arr = [];
 for (let i = 0; i < 2; i++) {
     arr[i] = function () {
         console.log(i); 
     }
 }
 arr[0]();	// 预期输出 0
 arr[1]();	// 预期输出 1
```

图解：关键点在于每次循环都会产生一个块级作用域，每个块级作用域中的变量都是不同的，函数执行时输出的是自己上一级（循环产生的块级作用域）作用域下的 i 值

![let面试题2](https://gitee.com/wlogan/pic-go-picture-bed/raw/master/images/20200907140620.png)

#### 4.2 var、let 和 const 的对比

![var&let&const区别](https://gitee.com/wlogan/pic-go-picture-bed/raw/master/images/20200930132524.png)

1. 变量提升

    **误区：**let 和 const 没有变量提升！

    let 和 const 定义的变量都会被提升，**但是不会被初始化**，不能被引用，不会像 var 定义的变量那样，初始值为 undefined。

    至于为什么 let 和 const 定义的变量不会被初始化呢？主要是因为 const。

    const，顾名思义：常量，const 的引用不应被改变。如果编译器把 const 初始化为 undefined，之后，又让它等于我们定义的那个值，就改变了 const 的引用。因此，委员会决定 let 和 const 虽然也会发生变量提升，但是没有任何初始值。

2. 块级作用域

    var、let 和 const 另外一个重要区别就是 let 和 const 只在块级作用域中有效

3. 循环中 i 的定义

---

### 5 JQuery



---

### 6 Ajax

#### 6.1 Ajax 的优缺点

##### 优点

- 局部刷新页面，减少用户心理和实际的等待时间，带来更好的体验；
- 减轻服务器的负担，按需取数据，最大程度减少冗余请求；
- 基于 xml 标准化，并被广泛支持，无需安装插件，进一步促进页面和数据的分离。

##### 缺点

- Ajax 大量使用了 JavaScript 和 Ajax 引擎，这些取决于浏览器的支持，在编写的时候考虑对浏览器的兼容性；
- 只是局部刷新，页面的后退按钮是没有用的；
- 对流媒体还有移动设备的支持不是太好等。

##### 用法

1. 创建 Ajax 对象（new XMLHttpRequest）

2. 判断数据传输方式（GET / POST）

3. 打开链接 open()

4. 发送 send()

5. 定义数据返回后的回调函数，里面的代码在 readystatechange 值改变时执行

    注意：这里 readyState 的值有五种，分别代表

    - 0：XMLHttpRequest 对象创建完成。「还没有调用 open() 方法」；
    - 1：XMLHttpRequest对象初始化完成。「已调用 send() 方法，正在发送请求」；
    - 2：请求已经发送。「send() 方法完成，已经收到全部响应内容」；
    - 3：服务器已经返回了数据（但是还没有被解析，可能只一段 http 报文）。「正在解析响应内容」；
    - 4：数据解析已经完成。「响应内容解析完成，可以在客户端调用了」。

```javascript
function loadXMLDoc() { // 点击事件
    var xmlhttp;
    // 1、创建XMLHttpRequest对象
    if (window.XMLHttpRequest) {
        // IE7+, Firefox, Chrome, Opera, Safari 浏览器执行代码
        xmlhttp = new XMLHttpRequest();
    } else {
        // IE6, IE5 浏览器执行代码
        xmlhttp = new ActiveXObject("Microsoft.XMLHTTP");
    }

    // 2、open方法表示初始化请求，此时并没有发送。
    xmlhttp.open("POST","/try/ajax/demo_post2.php",true);

    xmlhttp.setRequestHeader("Content-type","application/x-www-form-urlencoded");

    // 4、发送请求
    xmlhttp.send("fname=Henry&lname=Ford");

    // 3、当参数被传入服务器的时候，引用监听事件。
    xmlhttp.onreadystatechange = function() {
        // 判断 readyState 四种状态，当执行四步完成之后，并且返回的是200（成功）
        if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {          							document.getElementById("myDiv").innerHTML = xmlhttp.responseText;
        }
    }
}
```



---

### 7 Vue

#### 7.1 开发一个 Alert 组件，你可以先重点谈谈你的设计思路和实现方案

#### 7.2 Vue 的双向数据绑定原理

Vue 内部通过 Object.defineProperty 方法属性拦截的方式，把 data 对象里每个数据的读写转化成 getter / setter，当数据变化时通知视图更新。

采用数据劫持结合发布者-订阅者模式的方式，通过 Object.defineProperty() 来劫持各个属性的 setter，getter，在数据变动时发布消息给订阅者，触发相应的监听回调。

```html
 <!DOCTYPE html>
 <html lang="en">
 <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <title>Document</title>
     <style>
        
     </style>
 </head>
 <body>
    姓名：<span id="spanName"></span>
    <br >
    <input type="text" id="inpName">
    <script>
        let obj = {
            name: ''
        }
        // 深克隆一份 obj
        let newObj = JSON.parse(JSON.stringify(obj))
        Object.defineProperty(obj, 'name', {
            get() {
                return newObj.name
            },
            set(val) {
                if (val === newObj.name) return
                newObj.name = val
                observer()
            }
        })
        
        function observer() {
            spanName.innerHTML = obj.name
            inpName.value = obj.name
        }
        
        setTimeout(() => {
            obj.name = "Logan"
        }, 1000);
        
        inpName.oninput = function() {
            obj.name = this.value
        }
    </script>
 </body>
 </html>
```

Vue 3.0 实现方法

```html
 <!DOCTYPE html>
 <html lang="en">
 <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <title>Document</title>
     <style>
        
     </style>
 </head>
 <body>
    姓名：<span id="spanName"></span>
    <br >
    <input type="text" id="inpName">
    <script>
        let obj = {}
        obj = new Proxy(obj, {
            get(target, prop) {
                return target[prop]
            },
            set(target, prop, value) {
                target[prop] = value
                observer()
            }
        })
        
        function observer() {
            spanName.innerHTML = obj.name
            inpName.value = obj.name
        }
        
        setTimeout(() => {
            obj.name = "Logan"
        }, 1000);
        
        inpName.oninput = function() {
            obj.name = this.value
        }
    </script>
 </body>
 </html>
```



#### 7.3 为什么 Vue 中的 data 必须是一个函数

js 中只有函数构成作用域（对象和 for 等都不构成作用域），data 是一个函数时，每个组件都有自己的作用域，每个实例相互独立，不会相互影响。

如下：

```javascript
data: function () {
  return {
    count: 0
  }
}
```

而不是：

```javascript
data: {
  count: 0
}
```

#### 7.4 v-show 和 v-if 的区别

- v-show：不管条件是真还是假，第一次渲染的时候都会编译出来，也就是标签都会添加到DOM中。之后切换的时候，通过 display: none; 样式来显示隐藏元素。可以说只是改变css的样式，几乎不会影响什么性能。
- v-if：在首次渲染的时候，如果条件为假，什么也不操作，页面当作没有这些元素。当条件为真的时候，开始局部编译，动态的向 DOM 元素里面添加元素。当条件从真变为假的时候，开始局部编译，卸载这些元素，也就是删除。

性能方面：

- v-if 有更高的切换消耗，不适合做频繁的切换；
- v-show 有更高的初始渲染消耗，适合做频繁的切换。

#### 7.5 Vue 的生命周期

1. 挂载（初始化）
    - beforeCreate()：还不能访问 data、methods
    - created()：已将 data 和 methods 挂载到 vue 实例上
    - beforeMount()：模板编译完成，但未挂载，无法获取 DOM
    - mounted()：实例挂载完成，可以直接获取 DOM

1. 更新
    - beforeUpdate()：响应式数据更新时调用，发生在虚拟 DOM 打补丁之前
    - updated()：虚拟 DOM 重新渲染和打补丁之后调用，组件 DOM 已经更新
2. 销毁
    - beforeDestroy()：实例销毁之前调用，组件中数据、方法和指令还是可用状态
    - destroyed()：实例销毁后调用，组件中数据、方法和指令不可用

#### 7.6 Vue 组件之间的传值

- 父组件向子组件传值

    父组件以属性的形式绑定值到子组件身上，子组件用 props 接收。

    ```html
      <div id="app">
        <div>{{pmsg}}</div>
         <!-- 1、menu-item 在 APP中嵌套着，故 menu-item 为子组件 -->
         <!-- 给子组件传入一个静态的值 -->
        <menu-item title='来自父组件的值'></menu-item>
        <!-- 2、 需要动态的数据的时候 需要属性绑定的形式设置 此时 ptitle  来自父组件data 中的数据传的值可以是数字、对象、数组等等 -->
        <menu-item :title='ptitle' content='hello'></menu-item>
      </div>
    
      <script type="text/javascript">
        Vue.component('menu-item', {
          // 3、 子组件用属性 props 接收父组件传递过来的数据  
          props: ['title', 'content'],
          data: function() {
            return {
              msg: '子组件本身的数据'
            }
          },
          template: '<div>{{msg + "----" + title + "-----" + content}}</div>'
        });
        var vm = new Vue({
          el: '#app',
          data: {
            pmsg: '父组件中内容',
            ptitle: '动态绑定属性'
          }
        });
      </script>
    ```

- 子组件向父组件传值

    子组件用 $emit() 触发事件，$emit(自定义的名称，需要传递的数据)，父组件用 v-on 监听子组件的事件，用 $event 来接收传递过来的数据。

    ```html
     <div id="app">
        <div :style='{fontSize: fontSize + "px"}'>{{pmsg}}</div>
         <!-- 2 父组件用 v-on 监听子组件的事件
    		这里 enlarge-text 是从 $emit 中的第一个参数对应   handle 为对应的事件处理函数	-->	
        <menu-item :parr='parr' @enlarge-text='handle($event)'></menu-item>
      </div>
      <script type="text/javascript" src="js/vue.js"></script>
      <script type="text/javascript">
        /*
          子组件向父组件传值-携带参数
        */
        Vue.component('menu-item', {
          props: ['parr'],
          template: `
            <div>
              <ul>
                <li :key='index' v-for='(item,index) in parr'>{{item}}</li>
              </ul>
    			###  1、子组件用$emit()触发事件
    			### 第一个参数为 自定义的事件名称   第二个参数为需要传递的数据  
              <button @click='$emit("enlarge-text", 5)'>扩大父组件中字体大小</button>
              <button @click='$emit("enlarge-text", 10)'>扩大父组件中字体大小</button>
            </div>
          `
        });
        var vm = new Vue({
          el: '#app',
          data: {
            pmsg: '父组件中内容',
            parr: ['apple','orange','banana'],
            fontSize: 10
          },
          methods: {
            handle: function(val){
              // 扩大字体大小
              this.fontSize += val;
            }
          }
        });
      </script>
    
    ```

- 兄弟组件之间相互传值 / 两个没有关系的组件之间的传值

    兄弟之间传递数据需要借助于事件中心，通过事件中心传递数据。提供事件中心 var hub = new Vue()。

    - 传递数据方，通过一个事件触发 hub.$emit(方法名，传递的数据)
    - 接收数据方，通过在 mounted() {} 钩子函数中，触发 hub.$on(方法名，(接收的数据) => {})
    - 通过 hub.$off(方法名) 销毁之后将无法进行数据传递。

    ```html
     <div id="app">
        <div>父组件</div>
        <div>
          <button @click='handle'>销毁事件</button>
        </div>
        <test-tom></test-tom>
        <test-jerry></test-jerry>
      </div>
      <script type="text/javascript" src="js/vue.js"></script>
      <script type="text/javascript">
        /*
          兄弟组件之间数据传递
        */
        //1、 提供事件中心
        var hub = new Vue();
    
        Vue.component('test-tom', {
          data: function(){
            return {
              num: 0
            }
          },
          template: `
            <div>
              <div>TOM:{{num}}</div>
              <div>
                <button @click='handle'>点击</button>
              </div>
            </div>
          `,
          methods: {
            handle: function(){
              //2、传递数据方，通过一个事件触发hub.$emit(方法名，传递的数据)   触发兄弟组件的事件
              hub.$emit('jerry-event', 2);
            }
          },
          mounted: function() {
           // 3、接收数据方，通过mounted(){} 钩子中  触发hub.$on(方法名)
            hub.$on('tom-event', (val) => {
              this.num += val;
            });
          }
        });
        Vue.component('test-jerry', {
          data: function(){
            return {
              num: 0
            }
          },
          template: `
            <div>
              <div>JERRY:{{num}}</div>
              <div>
                <button @click='handle'>点击</button>
              </div>
            </div>
          `,
          methods: {
            handle: function(){
              //2、传递数据方，通过一个事件触发hub.$emit(方法名，传递的数据)   触发兄弟组件的事件
              hub.$emit('tom-event', 1);
            }
          },
          mounted: function() {
            // 3、接收数据方，通过mounted(){} 钩子中  触发hub.$on()方法名
            hub.$on('jerry-event', (val) => {
              this.num += val;
            });
          }
        });
        var vm = new Vue({
          el: '#app',
          data: {
            
          },
          methods: {
            handle: function(){
              //4、销毁事件 通过hub.$off()方法名销毁之后无法进行传递数据  
              hub.$off('tom-event');
              hub.$off('jerry-event');
            }
          }
        });
      </script>
    
    ```

#### 7.7 谈谈你对 vuex 的理解

应该围绕这 3 方面来一次性说清楚：

##### vuex 是什么？

vuex 是一个专为 vue.js 应用程序开发的状态管理模式。

##### vuex 的核心概念

vuex 有 5 个核心属性：state、mutations、actions、getters 和 modules

- state：存储数据；组件中用 this.$store.state.全局数据名称，就可以访问到数据；也可以按需导入 mapState 函数，然后映射为计算属性；
- mutations：更改 store 中的数据的唯一方法是提交 mutation；
- actions：异步操作只能在这里进行，通过提交 mutation 间接更改数据；
- getters：类似 vue 的计算属性，通过依赖进行缓存，只有它依赖的值发生了改变才会被重新计算；
- modules：将 store 分割成模块，每个模块都具有 state、mutations、actions 和 getters，还可以嵌套子模块。

传递数据流程：

- 通过调用 this.$store.commit() 的方法来触发 mutations 里面的方法；
- 通过调用 this.$store.dispatch() 来调用 actions 中的方法，actions 中通过 context.commit() 来触发 mutations 里面的方法；

#### 7.8 框架的特点和优势

##### 特点

- 响应式编程
- 组件化

##### 优势

轻量级框架、简单易学、双向数据绑定、组件化、数据和结构的分离、虚拟 DOM，运行速度快。

---

### 8 HTTP

#### 8.1 谈一谈 HTTP 协议优缺点

##### 优点

- 灵活可扩展
- 请求 - 应答模式
- 可靠传输
- 无状态

##### 缺点

- 无状态
- 明文传输
- 队头阻塞

#### 8.2 HTTP 1.0、1.1、2.0 之间的区别

##### HTTP 1.0

- 任何格式的内容都可以发送；
- 有 GET、POST 和 HEAD 方法；
- 每次通信都必须包括头信息和数据；
- 不支持断点续传；
- 请求消息中的 URL 并没有传递主机名。

##### HTTP 1.1

http1.1 是目前最为主流的 http 协议版本，从 1999 年发布至今，仍是主流的 http 协议版本。

- 引入了持久连接。也即是 TCP 连接默认不关闭，可以被多个请求复用，不用声明 Connection: keep-alive；
- 引入了管道机制。在同一个 TCP 连接里，客户端可以同时发送多个请求，提高效率；
- 支持断点续传。
- 新增 PUT、PATCH、OPTIONS、DELETE 和 CONNECT 方法；

##### HTTP 2.0

- **二进制分帧**。这是一次彻底的二进制协议，头信息和数据体都是二进制，并且统称为"帧"：头信息帧和数据帧；
- **头部压缩**。HTTP 1.1 版本会出现 **「User-Agent、Cookie、Accept、Server、Range」** 等字段可能会占用几百甚至几千字节，而 Body 却经常只有几十字节，所以导致头部偏重。HTTP 2.0 使用 `HPACK` 算法进行压缩；
- **多路复用**。复用 TCP 连接，在一个连接里，客户端和浏览器都可以同时发送多个请求或回应，且不用按顺序一一对应，这样子解决了队头阻塞的问题；
- **服务器推送**。 允许服务器未经请求，主动向客户端发送资源，即服务器推送；
- **请求优先级**。可以设置数据帧的优先级，让服务端先处理重要资源，优化用户体验。

#### 8.3 谈一谈你对 HTTP 2 的理解

##### 头部压缩 HPACK 算法

![img](https://gitee.com/wlogan/pic-go-picture-bed/raw/master/images/20201013163306.png)

类似于索引表

##### 多路复用

##### 服务器推送

##### 二进制分帧

#### 8.4 谈一谈 GET 和 POST 的区别

本质上，只是语义上的区别，GET 用于获取资源，POST 用于提交资源。

- 从缓存角度看，GET 请求后浏览器会主动缓存，POST 默认情况下不能；
- 从参数角度看，GET 请求一般放在 URL 中，POST 放在请求体中，因此相对较安全；
- 从编码角度看，GET 请求只能进行 URL 编码，只能接受 ASCII 码，而 POST 支持更多的编码类型；
- GET 请求会一次性发送请求报文，POST 请求通常分为 2 个 TCP 数据包，首先发 header 部分，如果服务器响应 100（指状态码），然后发 body 部分。

---

### 9 其他

#### 9.1 说一说什么是跨域，怎么解决

因为浏览器出于安全考虑，有同源策略。也就是说，如果**协议**、**域名**或者**端口**有一个不同就是跨域，Ajax 请求会失败！
为了防止 CSRF 攻击，有如下解决方案：

1. JSONP

    JSONP 的原理很简单，就是利用 <script> 标签没有跨域限制的漏洞。

    通过 <script> 标签指向一个需要访问的地址并提供一个回调函数来接收数据当需要通讯时。

    ```javascript
    <script src="http://domain/api?param1=a&param2=b&callback=jsonp"></script>
    <script>
        function jsonp(data) {
        console.log(data)
    }
    </script>
    ```

     

#### 9.2 说一说 sessionStorage 和 localStorage 还有 cookie 的区别和优缺点 

- 相同点：都是保存在浏览器端的、同源的

- 不同点：

    - sessionStorage：仅在当前浏览器窗口关闭之前有效；

        localStorage：始终有效，窗口或浏览器关闭也一直保存，本地存储，因此用作持久数据； 

    - cookie 数据始终在同源的 http 请求中携带（即使不需要），即 cookie 在浏览器和服务器间来回传递。

        cookie 数据还有路径（path）的概念，可以限制 cookie 只属于某个路径下

        sessionStorage 和 localStorage 不会自动把数据发送给服务器，仅在本地保存。

    -  存储大小限制也不同，cookie 数据不能超过 4K，sessionStorage 和 localStorage 可以达到 5M

    -  作用域不同

        sessionStorage：不在不同的浏览器窗口中共享，即使是同一个页面；

        localstorage：在所有同源窗口中都是共享的；也就是说只要浏览器不关闭，数据仍然存在；

        cookie: 也是在所有同源窗口中都是共享的.也就是说只要浏览器不关闭，数据仍然存在。

#### 9.3 Promise是什么，解决了什么，之前怎么实现的

- Promise 是异步编程的一种解决方案，比传统的解决方案（回调函数和事件）更合理和更强大。
- 解决了之前在请求中回调请求产生的**回调地狱**，使得现在的代码更加合理更加优雅，也更加容易定位查找问题。




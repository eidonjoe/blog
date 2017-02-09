
* 如何遍历对象,使原型中的属性不被遍历出来

    > 通过hasOwnProperty检测属性是否存在于对象实例中还是存在于原型中
    ```javascript
        function eachObj() {
        	this.a = 'aaa';
        	this.b = 'bbb';
        	this.c = 'ccc';
        }
        eachObj.prototype.aaa = 'protocccc';
        var obj = new eachObj();
        for(var i in obj ) {
        	console.log(i,obj[i]);
        	if (obj.hasOwnProperty(i)) {
        		// 属性存在于对象实例中
        		console.log(i,obj[i]);
        	}
        }
    ```

* 垂直居中,display: table与table-cell的区别

  > table-cell与表格中<td>标签表现相同
    如果只对元素设置display: table-cell而不给父元素设置display: table以及display: table-row属性等,table-cell表现为普通块级元素
    同时继承table的一些特性,对高度敏感,对margin不敏感
    
* 如何获取当前元素在页面中的位置
    >   使用元素的offsetLeft与offsetTop属性可以获取元素与父元素左上角的距离
	    或直接使用getBoundingClientRect()方法,该方法返回一个对象,其中包含left,top,right,bottom,分别对应了该元素的左上角和右下角相对于浏览器窗口（viewport）左上角的距离。

* 如何使用fis进行数据模拟

* css定位相关知识
    >	先设置两个普通的div
	```html
	<div class="a"></div>
	<div class="b"></div>
	```
	然后设置两个元素的宽高
	```css
	.a {
	  width: 100px;
	  height: 100px;
	  background-color: red;
	}
	.b {
	  width: 100px;
	  height: 100px;
	  background-color: blue;
	}
	```
	![normal](http://7xrltq.com1.z0.glb.clouddn.com/position_normal.jpeg)
	接下来将a元素position设置为absolute,并设置top与left属性
	position: absolute;会使元素脱离文档流,从而不再占据先前的文档位置,导致其后面的元素重新排列
	
	```css
	.a {
	  width: 100px;
	  height: 100px;
	  background-color: red;
	  position: absolute;
	  left:100px;
	  top:100px;
	}
	```
	![absolute](http://7xrltq.com1.z0.glb.clouddn.com/postion_absolute.jpeg)

	重新改变a元素position属性,将其设置为relative,top,left不变
	position: relative;不会改变文档流,只改变当前元素所处位置,相对于先前所在的文档位置进行定位,而其他元素正常排列
	```css
	.a {
	  width: 100px;
	  height: 100px;
	  background-color: red;
	  position: relative;
	  left:100px;
	  top:100px;
	}
	```
	![relative](http://7xrltq.com1.z0.glb.clouddn.com/position_relative.jpeg)
	
* 事件委托
	> 利用冒泡机制,对多个需要添加事件处理程序的元素添加一个统一的事件处理程序,这种方式称为事件委托.
* em rem 百分比的区别
* localStorage 与sessionStorage 和cookie 的区别,localStorage和cookie的优劣分别在哪

	> localStorage 跨越会话存储数据,客户端持久保存用户数据的数据的方案,有访问限制;sessionStorage存储某个特定会话数据,浏览器关闭即删除;cookie浏览器Http Cookie客户端存储会话信息,由服务器响应设置请求头
	
	> localStorage不安全,存储大小为2.5MB-5MB,可以触发storage事件; cookie可以通过设置secure来通过https传输,存储大小2KB,可以指定失效时间
* 清除浮动的几种方法
* 如何实现节流函数
	> 某些事件会在用户操作的过程中连续触发,如果在事件处理程序内部尝试进行复杂的运算操作或是进行DOM操作,很可能引起浏览器崩溃
	所以要控制事件处理程序不可以在没有时间间隔的情况下连续重复执行
	
	* 节流函数实现
	```javascript 
		function throttle(method, context) {
			clearTimeout(method.tId);
			method.tId = setTimeout(function(){
				method.call(context);
			}, 100)
		}
	```
	> > throttle()函数的第一个参数是指函数在哪个作用域中执行,函数在执行时会先清除在该作用域中设置的定时器,接下来创建一个新的定时器.第二个参数用来确保定时器代码可以在合适的环境中执行,若省略第二个参数则会在全局作用域中执行该方法.
	
	//注: setTimeout()中用到的函数环境总是window,所以若想在函数内部改变函数环境,可以传入上下文或用that存储this对象
	

## 编程:
* 排序  冒泡排序的优化
* 事件绑定的兼容处理
* 区分数组与对象

	1.Array.isArray() // es5
	
	2.toString.call(value) == "[object Array]"
	
	```javascript
		function isArray (value) {
			return Object.prototype.toString.call(value) == "[object Array]"
		}
	```
	3.通过构造函数判断, arr.constructor; // Array	
	4.instanceof Array
* mongodb分页的实现,统计的实现
* 如何在前端实现require,AMD规范
* 在浏览器的不同tab间如何进行通知
* css实现为ul下的单数li添加指定样式
* navigator有哪些属性
* BOM对象除了navigator还有那些
* 进行页面跳转的方法
* 实现add(2)(3) = 5 函数柯里化 函数式编程
* nodejs如何查找依赖模块
* 如何获取url?后面的参数
* 如何获取url#后面的参数
* 在url后面加#并回车页面是否会刷新,增加参数后是否会刷新
* spa的实现原理
* 如何解决跨域问题,有几种解决办法
* jsonp的原理是什么
* 如何动态创建并向页面中添加脚本
* 如何定义自定义事件,如何触发自定义事件 
* async defer
	
	简单讲就是 没有 defer 或 async，浏览器会立即加载并执行指定的脚本
	
	async 和	defer都是异步加载,区别在于async是在脚本加载完成之后立即执行, 而defer会延迟执行, 即在所有页面元素渲染完成后加载
	
	先来试个一句话解释仨，当浏览器碰到 script 脚本的时候：

	<script src="script.js"></script>
	没有 defer 或 async，浏览器会立即加载并执行指定的脚本，“立即”指的是在渲染该 script 标签之下的文档元素之前，也就是说不等待后续载入的文档元素，读到就加载并执行。
	<script async src="script.js"></script>
	有 async，加载和渲染后续文档元素的过程将和 script.js 的加载与执行并行进行（异步）。
	<script defer src="myscript.js"></script>
	有 defer，加载后续文档元素的过程将和 script.js 的加载并行进行（异步），但是 script.js 的执行要在所有元素解析完成之后，DOMContentLoaded 事件触发之前完成。
	然后从实用角度来说呢，首先把所有脚本都丢到 </body> 之前是最佳实践，因为对于旧浏览器来说这是唯一的优化选择，此法可保证非脚本的其他一切元素能够以最快的速度得到加载和解析。
	
	![async defer](http://7xrltq.com1.z0.glb.clouddn.com/async-defer.jpeg)
	
	蓝色线代表网络读取，红色线代表执行时间，这俩都是针对脚本的；绿色线代表 HTML 解析。

	此图告诉我们以下几个要点：

	1.defer 和 async 在网络读取（下载）这块儿是一样的，都是异步的（相较于 HTML 解析）
	2.它俩的差别在于脚本下载完之后何时执行，显然 defer 是最接近我们对于应用脚本加载和执行的要求的
	3.关于 defer，此图未尽之处在于它是按照加载顺序执行脚本的，这一点要善加利用
	4.async 则是一个乱序执行的主，反正对它来说脚本的加载和执行是紧紧挨着的，所以不管你声明的顺序如何，只要它加载完了就会立刻执行
	5.仔细想想，async 对于应用脚本的用处不大，因为它完全不考虑依赖（哪怕是最低级的顺序执行），不过它对于那些可以不依赖任何脚本或不被任何脚本依赖的脚本来说却是非常合适的，最典型的例子：Google Analytics
* 如何编写Jquery插件
* 如何向页面中添加一个节点
	> 
	```javascript
	var body = document.getElementsByTagName('body')[0]
	var div = document.createelement('div');
	div.setAttribute('id',1)
	body.appendChild(div)
	```
	





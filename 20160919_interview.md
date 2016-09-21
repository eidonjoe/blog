
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
* 事件委托
* em rem 百分比的区别
* localStorage 与sessionStorage 和cookie 的区别,localStorage和cookie的优劣分别在哪
* 清除浮动的几种方法
* 如何实现节流函数

## 编程:
* 排序  冒泡排序的优化
* 事件绑定的兼容处理
* 区分数组与对象


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





# angular2 江志成(雪狼) ThoughtWorker,Google开发技术专家,Angular官方文档翻译者,Angular中文社区公众号维护者

## 应用的成长 

初始化  npm g npm c  路由  先搭建原型 model list show

angular2 默认样式均为局部化样式,只影响单独组件 维护性更高

angular2 协同开发, 定义usermodel 指定强类型, 提取服务 ng s 保证数据一致,service需要加入Model中的provider中才会生效,
依赖注入不在根据名字进行注入,而是根据类型(?),

重构++阶段, async ng2 管道,ng1 过滤器


## 亮点 
	* 工程化,依赖注入(?)
	* 现代化,服务端渲染,native渲染
	* 集成化 ng1 社区组件居多, ng2 内置多种官方组件
	* 模块化 ng2 本身的模块化, 数据流抽象成标准接口,依赖注入不限于ng2

## 从ng1到ng2 
	* AoT 预编译, 编译模板 提速
	* 服务端渲染, 支持seo 提速
	* typeScript 提高质量
	* WebWorker 可以在辅助线程中进行运行,而不影响页面进程
	* 更好的路由和表单 对ng1的强化和补充,reactive forms 模型驱动表单,可以直接由后端渲染表单,动态表单
	* 对ng1 进行简化 内置指令从70减少到20,由指令变为绑定
	* 测试的简化, 
	* 更简单的依赖注入,名字改为类型
	* cli 
	* 官方风格指南

## 案例展示
	* iFish 架构 => ng2 + java 
    * 快速原型
    * v站论坛 基于定制版cli   参与开发 1.ng2相关文章,2.代码开发

## 新技术新领域

	* AoT编译
	* 服务端渲染
	* NativeScript整合
	* RxJs整合 数据流代替promise
	* PWA的支持 间接式应用,内置壳程序

## 社区建设 
	* 4000+qq群成员
	* 3W 每日pv
	* 1186/week 公众号关注人数
	* 2.5 year 开发时间
	* 55 alpha + 18 beta + 8 rc(?) 版本
	* 5651 commit

## 开发资源
	* Augury chrome测试插件
	* IDE webstorm vsc
	* Starter angular2-webpack-starter
	* cli 
	* @types ts辅助开发
	* 组件库 primeng Material 2
	* 资源大全(英文)

## 学习资源
	* 英文官网 angular.io
	* 中文官网 angular.cn
	* 中文社区公众号 Angular中文社区
	* 知乎 "Angular2" 话题
	* github
		* abgular/angular
		* angular-bbs/all(*)
		* 破狼ng2个人博客
## Q&A

	* es6 支持,ts编译
	* 移动端支持性,
	* 选型 ng2 java思想较多,后端强力依赖注入比较适合理解,适合组内有强大的后端支持(java,C#).
		长期维护并且团队分工明确,样式,页面结构分开开发,在调试上不会互相影响,内部耦合度低


# 基于FLUX架构的项目开发 蚂蚁金服 悠鹤 负责支付宝社交H5开发 

## 传统开发架构 MVC(MM) 
	* MVC应用变得复杂和难以扩展, 在model和view数据流动关注过多

	* 关注点分离 

## FLUX解决传统开发痛点
	* 核心 一个简单的约定,store的改变只能由action发起
	* 单向数据流,view发起,通过dispatcher 传到 action改变store,不能通过view直接改变store
	* 统一调度, app dispatcher
	* 可预测
	* 函数式编程, 纯函数,非纯函数
	react和vue是对视图的抽象,FLUX是对用户行为的抽象
## FLUX应用主要实现

	* react + redux
	* vue + vuex
	UI =f(state)  state的纯函数,纯函数利于测试(?)
	(state, action) =>(state)

	redux是一个状态可预测的容器

	react + redux数据流动


# 如何做好技术演讲 杨疯疯

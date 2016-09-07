## 坑and脱坑
#### passwort-wechat

wechat只支持pc授权,不支持手机版,更改包源码,重新发布npm包

##### ccap ==> captchagen
需要系统依赖输出改为依赖canvas包输出
fork captchagen 定制验证码宽高,输出点,输出线,背景颜色,背景图片

#### 内存泄露
首先检查代码中是否有死循环,或重复创建的模块对象,发现并不存在语法问题
之后进行ab压力测试测试接口内存增长速度,通过node-inspector 集成的v8-profiler功能定位到session被重复创建,
检查程序中session中间件初始代码,发现对所有路由均初始化了session,而项目中有些对其他服务提供的接口,这部分接口通过服务器内部调用,req.header中不存在cookie
导致session中间件初始化失败,从而不停重复加载中间件
解决办法, 对指定路由加载session中间件,
更改后问题修复

所有路由增加session ==> 特定路由开启session

#### 首页打包
**.js ==> 打包指定js

#### yog加载配置文件

指定-e参数,否则默认加载dev

#### 修复手机版Safari浏览器input光标过大,

光标会根据input框高度显示,而不是字号值,密码框高度需要比字号稍大,safari对属性为password的字段与其他实现不同

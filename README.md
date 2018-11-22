#本地开发
* gulp
#发布
* gulp build
#清理
* gulp clean
##待处理事件
把flow配置到webpack
https://www.jianshu.com/p/81b51c653301
##进度
tree shaking未学习 . 修改文字本地用fetch获取的到么
* * *

#项目文件
* 所有文件名一律使用小写和中横线（兼容部分服务器）
* wxml、scss、json文件优先使用双引号
* js文件优先使用单引号
* 配置文件使用双引号

#wxml
* 事件绑定加分号，bind:tap
* 指定属性值时则对应使用连字符写法（component-tag-name property-name="attr value"）
* 应用于数据绑定时采用驼峰写法（attr="{{propertyName}}"）
* 属性应当按照顺序排列，加强易读性 class --> id,name --> data-* --> wx:for --> bind:* --> others

#scss
* gulp之后会监听项目中的scss文件，并在对应目录下生成同名的wxss文件以供微信开发者工具使用
* class一律使用小写和下划线拼接（方便双击选择）
* 属性书写顺序, 建议遵循 flex属性-->布局定位属性-->自身属性-->文本属性-->其他属性
* 组件最外层标签默认不写间距，由引入的页面/组件设定
* @minxin写在assets/style/mixin.scss中，在需要使用的地方import
* 页面样式文件可以使用全局样式，组件样式文件需要自行import需要的样式
* z-index: popup=>9
* iconfont以设计稿中的高度为基准填写font-size
* 文本的line-height以font-size的1.25倍左右为参考,当出现同一行有不同size的情况时，以line-height高的一方为准

#js
* 命名方式优先使用驼峰写法（propertyName）
* import进来的模块名大写首字母（Util）
* form表单的元素如果有相同name的情况，在后面加下划线，跟元素识别字符串，（verifycode_message）
* 默认使用export default，不需要在import时指定模块中的方法名，如果需要使用不同的方法，则在default中统一导出
* 私有方法放在class外，使用下划线_开头
* 在需要new的情况下优先使用语法糖class写法
* 声明周期onload书写顺序，config.isFile=>console.log(打印页面入参)=>其他
* 交付页面的时候，控制台只有3种数据输出，onload，request，submit(_result)

#page
* 事件的书写顺序遵循 生命周期-->数据请求-->页面交互-->组件响应-->逻辑事件-->全局通用
* 生命周期：按照官方文档的顺序书写
* 数据请求: 以dev开头
* 页面交互：以tap、change等事件名开头，例：bind:tap => tapTest
* 组件响应：以listen开头
* 逻辑事件：以下划线_开头
* 全局通用：showDialog、closeDialog、showPopup、_（等等）_

#utils
* 以render.开头的文件，可以在任意地方const App=getApp()使用

#原生组件
* 不使用navigator，统一使用a-href
* form表单中的name如果有重复的，在name之后跟#自定义，例：name='tel',name='tel#another'

#自定义组件
* 在 properties 定义段中，属性名采用驼峰写法（propertyName）
* 组件中不会被全局样式（app.wxss影响），如果需要全局样式，自行import对应style中的文件
* trigger事件以call开头，页面中对应的组件响应事件以listen开头
* form-开头的文件会继承form组件的提交事件，根据name和value值响应

* * *

#页面
* index：目录页，便捷开发
* sample：功能样品页，便捷开发

#自定义组件：
* a-href：跳转链接，取代navigate
* back-top：回到顶部
* count-box: 加减框
* dialog：自定义弹出框
* delivery-select：选择送货区域
* form-input：自定义输入栏
* popup-template：弹窗模板
* verifycode：验证码
* tabbar：自定义tabbar
* pdt-box：产品box_（未开发）_
* search-input：搜索输入栏_（未开发）_

#utils
* check-auth：判断是否能够获取到该权限，执行相应回调
* check-form：表单验证，返回结果数组，由name对应config中的配置
* check-openid：用户身份验证，成功则返回openid，失败则返回用户code
* create-timer：倒计时
* util：方法集合
* render.api：微信API，可由全局App调用
* render.href：页面跳转，可由全局App调用
* render.request：接口请求，可由全局App调用
* render.store：数据存储，可由全局App调用

#behaviors:
* popup
* relations

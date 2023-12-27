vue3

0. 安装
	0. npm init vue@latest
	1. cd project_name && npm install
	2. npm run dev

1. 目录
	0. package.json 		项目包文件, 类似php中的composer.json
	1. vite.config.js 		项目的配置文件, 基于vite的配置
	2. index.html			单页入口, 提供id为app的挂载点
	3. src/main.js 			入口文件, createApp 函数创建的应用实例
	4. src/app.vue 			根组件, SFC单文件组件 script - template - style

2. 常用组件
	0. vite 


3. 组合式API
	0. reactive 和 ref
		0. 都是用函数调用的方式生成响应式数据
		1. reactive 不能处理简单类型的数据
		2. ref 参数类型支持更好, 但是必须通过 .value 访问修改
		3. ref 函数的内部实现依赖于 reactive 函数
		4. ref 函数功能更灵活, 建议使用

	1. computed 计算属性函数
		0. 计算属性中u应该有 "副作用", 比如异步请求/修改dom
		1. 避免直接修改计算属性的值, 计算属性应该是只读的

	2. watch 侦听变化
		0. 侦听单个
		1. 侦听多个
		2. 立即执行 immediate, 在侦听器创建时立即触发回调, 响应式数据变化之后继续执行回调
		3. 深度侦听 deep, watch监听的 ref 对象默认是浅层侦听, 直接修改嵌套的对象属性不会触发回调,需要开启 deep 选项, 性能损耗较大, 尽量不开启deep
		4. 精确侦听

	3. 生命周期函数
        0. onBeforeMount()              注册一个钩子，在组件被挂载之前被调用
        1. onMounted()                  注册一个回调函数，在组件挂载完成后执行
        2. onBeforeUpdate()             注册一个钩子，在组件即将因为响应式状态变更而更新其 DOM 树之前调用
        3. onUpdated()                  注册一个回调函数，在组件因为响应式状态变更而更新其 DOM 树之后调用
        4. onActivated()                注册一个回调函数，若组件实例是 <KeepAlive> 缓存树的一部分，当组件被插入到 DOM 中时调用
        5. onDeactivated()              注册一个回调函数，若组件实例是 <KeepAlive> 缓存树的一部分，当组件从 DOM 中被移除时调用
        6. onBeforeUnmount()            注册一个钩子，在组件实例被卸载之前调用
        7. onUnmounted()                注册一个回调函数，在组件实例被卸载之后调用

        8. onErrorCaptured()            注册一个钩子，在捕获了后代组件传递的错误时调用

        9. SSR only
            0. onServerPrefetch()       注册一个异步函数，在组件实例在服务器上被渲染之前调用。

        10. Dev only:
            0. onRenderTracked()        注册一个调试钩子，当响应式依赖的变更触发了组件渲染时调用
            1. onRenderTriggered()      注册一个调试钩子，当响应式依赖的变更触发了组件渲染时调用

	4. 父传子 
		0. 父组件中给子组件绑定属性
		1. 子组件内部通过 defineProps 选项接手

	5. 子传父
		0. 父组件中给子组件标签通过 @ 绑定事件
		1. 子组件内部通过 defineEmit 方法触发事件

	6. 模板引用
		0. 通过 ref 标识绑定 ref 对象
		1. 在<script setup>语法糖下, 组件内部的属性和方法是不开放给父组件访问的, 可以通过 defineExpose 暴露制定的方法/属性给父组件

	7. 跨层组件通信
		0. privide	提供数据
		1. inject	获取数据
`onMounted` 钩子可以用来在组件完成初始渲染并创建 DOM 节点后运行代码

当调用 `onMounted` 时，Vue 会自动将回调函数注册到当前正被初始化的组件实例上。这意味着这些钩子应当在组件初始化时被**同步**注册。
![[lifecycle_zh-CN.FtDDVyNA.png]]
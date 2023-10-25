# 简历调优

## 改进方向

### 团队 leader
- [ ] 架构能力
- [ ] 管理能力
- [ ] 项目排期
- [ ] 团队沟通
- 技术选型专题
  - [ ] skypack
  - [ ] bestofjs
  - [ ] npm trends
  - [ ] npm.devtool

### 团队协作
- [x] 内部基建、低代码、组件库
- [x] 规范 pr 和 commit

### 数据监控、运营管理
- [x] 使用数据埋点
- [ ] 开发埋点监控平台、SDK、浏览器 DevTools 插件
- [ ] 全链路日志，全局唯一请求
- [ ] 

### 内部工具、前端基建
- [x] vite webpack plugin
- [x] devops
- [x] 推动团队代码规范
- [x] 技术选型
- [ ] 封装脚手架
- [ ] 主推动可视化组件库、规范、流程、团队文化建设
- [ ] 微前端
- [ ] vscode 研发插件
- [ ] 大前端统一脚手架

### 研发提效
- [ ] devtool直接打开文件原理
- [ ] 

### 测试优化
- [ ] 单元测试
- [ ] 自动化测试
- [ ] UI 测试、设计走查自动化
- [ ] 

### 性能优化
- [x] 打包性能优化
- [x] 前端接入前端性能监控
- [x] 渲染优化、虚拟列表
- [x] 大文件上传
- [ ] 性能优化 监控  全链路性能优化 性能检测 Lighthouse 计算方式
- [ ] web 资源在页面空闲时预加载
  - [ ] 页面空闲检测
```js
// requestIdleCallback，支持在每帧绘制空闲期执行一个回调函数，但不能确保一定执行。

// 所以我们只能自己想办法判断了，思路其实也比较简单，浏览器的渲染进程有js引擎和UI引擎这两个线程，只要这两个线程是空闲的，我们就认为页面是空闲的，这应该是行得通的。

// 检测js线程空闲
const d1 = new Date();
setTimeout(()=＞{ 
    const offset = new Date() - d1;
    if (offset < 25 ) { 
      // JS线程空闲 
    }
}), 20);


// 启动一个延时函数，查看真正执行时候的延时是多少，如果延时很大，那说明当前js引擎繁忙。如果小于某个阈值，那说明js引擎空闲。

// 这个阈值该如何确定呢？统计真实用户的情况肯定是最准确的，所以我们用一个空闲页面统计了用户的延时均值，最终确定为5ms。

// 同样的思路，UI引擎的空闲也可以检测出来：

// 检测UI线程空闲
const d1 = new Date();
requestAnimationFrame(()=＞{
    const offset = new Date() - d1;
    if ( offset < 30 ) { 
      // UI线程空闲 
    }
})

// 阈值的确定也是统计的真实用户均值，最终确定为30ms。

// 有了这两项检测，我们就拿到了页面的“空闲时刻”。那如何“尽早的”拿到呢？做法相对简单，我们在页面加载完后用setInterval启动轮询，每隔1秒检测一次，一但检测到空闲，就进行资源预加载。
```
- 高性能专题
  - [ ] web worker
  - [ ] wasm
  - [ ] gpu.js
  - [ ] node-gyp
  - [ ] headless-gl
  - [ ] node-webgl
  - [ ] node-bindings

### 日志方向
- [ ] 故障检测，错误上报

### 页面改进、用户体验
- [x] 移动端适配
- [ ] pwa
- [ ] 浏览器缓存 sharedWorker
- [ ] [前端首屏优化 | 借助客户端能力提升 H5 首屏的 8 个手段](http://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247513844&idx=1&sn=4e6e5e3f1fea79c3c8f2b69446dbd5eb&chksm=eb078e8ddc70079b1054a379849f78e49ffd49c15f62a5c9c60e88a7d99a32ae304d11000433&mpshare=1&scene=23&srcid=08284EHQ1gTmTXPSPZTEBE2M&sharer_sharetime=1693221457937&sharer_shareid=ce373000e59a48726434cd087861e928#rd)
- [ ] 浏览器兼容性
- [ ] 动效动画
- [ ] ssr
- [ ] 页面间通信
- [ ] 字体显示问题，衬线体、无衬线体，font-weight
- [ ] CDN
- [ ] NGINX gzip、brotli
- [ ] 安全三角、嵌套菜单
- [ ] 

### 多端开发、大前端
- [ ] 浏览器拓展插件
- [ ] 客户端跨端 Electron
- [ ] 移动端跨端开发 expo rn
- [x] 跨端 uniapp
- [ ] websocket
- [ ] 小程序热更新
- [ ] webview 性能优化，预加载
- [ ] 小程序离线包

### 后端方向
- [ ] node后端、nestjs
- [ ] 微服务
- [ ] 各种中间件
- [ ] 服务网关、灰度策略
- [ ] 研发泳道
- [ ] serverless
- [ ] 边缘计算

### 客户端方向
- [ ] 加壳/加密
- [ ] 跨平台
- [ ] 程序通信
- [ ] 异构
- [ ] 

### 底层方向
- [ ] Windows api
- [ ] 

### 数据库方向
- [ ] 表字段冗余
- [ ] 数据一致性
- [ ] 幂等性
- [ ] 日志
- [ ] 

### 基础工具方向
- [ ] bun、deno
- [ ] typescript 增强
- [ ] tsrpc
- [ ] 

### 对接第三方平台
- [ ] wxpay、alipay
- [ ] QQ OAuth2.0
- [ ] SSO
- [ ] 双 token
- [ ] 

### 企业级方向
- [ ] cas、oauth、ladp、http ba
- [ ] 全局水印
- [ ] 

### 真实项目经历
- [ ] 开发、测试、预发、生产上线流程
- [ ] 错误回滚
- [ ] 故障演练
- [ ] 泳道开发
- [ ] prd评审
- [ ] 技术方案评审

### 特殊功能方向
- [ ] UI 设计工具
- [ ] design2code
- [ ] figma、skech 设计代码组件库
- [ ] figma 设计工具
- [ ] 操作 Excel PDF word PPT
- [ ] 

### 开源
- [x] 开源贡献
- [ ] 开源社区爱好者、有自己的开源项目者优先
- [ ] npm发包
- [ ] 组件库
- [ ] 可视化图标、geo、d3

### 产品、UI、UED、项目管理
- [x] 有产品、交互、设计等方向能力与经验者
- [ ] 参与产品功能开发的需求评审
- [ ] 结合应用场景和客户需求，提出专业合理的可视化方案建议
- [ ] 项目管理 项目排期 工程管理

### DevOps、运维部署优化
- [x] ansible 自动化部署，ansible-galaxy
- [x] Docker、Dockerfile、Docker Compose 自动化集群
- [ ] k8s
- [ ] jekins
- [ ] 虚拟化 kubevirt、libvirt

### 招聘要求
- [ ] 对某一领域有深入理解包括但不限于$/浏览器内核/性能优化/ reacti源码vue源码


## 参考文章

- [页面加载链路](https://juejin.cn/post/7249665163242307640)

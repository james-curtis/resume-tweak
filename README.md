# 简历调优

## 改进方向

### 团队 leader 意识
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
- [ ] [工程化](https://mp.weixin.qq.com/s/VVqom0saUCED2-4D2mAAxw)
- [ ] 文档体验优化
  - [ ] [Asciinema 终端录屏](https://mp.weixin.qq.com/s/GLQvRRvVjbtIv1FsDbpsDg)

### 数据监控、运营管理
- [x] 使用数据埋点
- [ ] 开发埋点监控平台、SDK、浏览器 DevTools 插件
- [ ] 性能优化 监控  全链路性能优化 性能检测 Lighthouse 计算方式
  - [ ] [前端监控SDK web-see](https://github.com/xy-sea/web-see)
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
  - [微前端源码剖析](https://www.yangyitao.com/microfe/)
- [ ] vscode 研发插件
- [ ] 大前端统一脚手架
- [ ] [devtool 跳转 ide](https://mp.weixin.qq.com/s/lW_VWn9dPZyMNgTfHA4Nqw)

- [不同打包工具下的环境变量配置方式对比](https://mp.weixin.qq.com/s/nXQSBNxIuiCkzhIKXOQCxA)

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
- [ ] [performance、memory indicator经验](https://mp.weixin.qq.com/s/s4mGvONAs-2BhPEcUOI7Wg)
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

### 技术负债治理
- [ ] 登录无限跳转轮询

### 日志方向
- [ ] 故障检测，错误上报
- [ ] 离线解析 sourcemap cli 参考：https://github.com/7ippo/sourcemapping
- [ ] sourcemap 可视化
  - https://github.com/evanw/source-map-visualization
  - https://github.com/sokra/source-map-visualization/
- [ ] chrome debug protocol | v8 debug protocol
  - https://juejin.cn/post/7096811694277525511#heading-19

### 页面改进、用户体验
- [x] 移动端适配
- [ ] pwa
- [ ] 浏览器缓存 sharedWorker
- [ ] [前端首屏优化 | 借助客户端能力提升 H5 首屏的 8 个手段](https://mp.weixin.qq.com/s/kYUrysBeVIqph4UAaUCNEA)
- [ ] 浏览器兼容性
- [ ] 动效动画
- [ ] ssr
- [ ] esr https://juejin.cn/post/7031570308293197837#heading-33
- [ ] 页面间通信
- [ ] 字体显示问题，衬线体、无衬线体，font-weight
  - [ ] 无极字体、可变字体
    - [突破限制，CSS font-variation 可变字体的魅力](https://www.cnblogs.com/coco1s/p/15944634.html)
    - 字体系列 css 属性 https://developer.mozilla.org/en-US/docs/Web/CSS/font-variation-settings
- [ ] CDN
- [ ] NGINX gzip、brotli
- [ ] 安全三角、嵌套菜单
- [ ] [页面版本更新提示](https://mp.weixin.qq.com/s/PT0PZ3S1Cvh2nltcIKwa3g)

### 异常兜底
- [ ] 页面白屏监控
- [ ] 

### 多端开发、大前端、小程序系列
- [ ] 浏览器拓展插件
- [ ] 客户端跨端 Electron
- [ ] 移动端跨端开发 expo rn
- [x] 跨端 uniapp
  - [uniapp 项目开发经验总结](https://mp.weixin.qq.com/s/rVRtbMSTOHEB6pRJZvB9fA)
- [ ] websocket
- [ ] 小程序热更新
- [ ] webview 性能优化，预加载
- [ ] 小程序离线包
- [ ] 拉起其他 app

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
- [ ] 内部 office
  - [开发一个腾讯文档要多久？借助 Luckysheet，仅需 3 分钟！](https://mp.weixin.qq.com/s/gBMN9fJ10m9ioO5O3IlZHQ)

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

### canvas
- [ ] https://github.com/LHRUN/paint-board
- [ ] https://github.com/linghuam/myblog/blob/master/source/_others/前端面试-图形库.md
- [ ] [轻量级、可插拔、OOP 式图形编辑器开发引擎](https://mp.weixin.qq.com/s/-jPESollUyoGjZZ8Q6_oTA)

### JS engine
- [ ] 【深度】扒开V8引擎的源码，我找到了你们想要的前端算法 https://juejin.cn/post/6844903935375835150?from=search-suggest
- [ ] promise.then 中 return Promise.resolve 后，发生了什么？ https://www.zhihu.com/question/453677175/answer/1841325386
- [ ] V8 Promise源码全面解读 https://juejin.cn/post/7055202073511460895#heading-39
- [ ] 微任务终极考验，一文讲解async/await转换Promise https://zhuanlan.zhihu.com/p/450906325

### 浏览器组成原理
- [ ] [浏览器是如何渲染页面的？](https://open.alipay.com/portal/forum/post/108901030)
### 招聘要求
- [ ] 对某一领域有深入理解包括但不限于$/浏览器内核/性能优化/ reacti源码vue源码

### JS 深度专项
- [ ] 事件循环
  - [揭开事件循环的神秘面纱](https://mp.weixin.qq.com/s/zDUqVqPH7_DxuEz9ovs-OA)
- [ ] promise
  - [40道Promise输出题，你都会了吗？](https://juejin.cn/post/7151636219036696613#heading-41)
  - [你不知道的 async、await 魔鬼细节](https://www.tais3.com/javascript/2268.html#:~:text=4%E3%80%81%E6%80%BB%E7%BB%93)

### debug
- [67 Weird Debugging Tricks Your Browser Doesn't Want You to Know](https://alan.norbauer.com/articles/browser-debugging-tricks)

### 框架源码
- [ ] [跟着我，从0实现React18](https://github.com/BetaSu/big-react)
- [ ] [「React技术揭秘」 一本自顶向下的React源码分析书](https://github.com/BetaSu/just-react?tab=readme-ov-file)
- [ ] [Vue.js 技术揭秘](https://ustbhuangyi.github.io/vue-analysis/)

## 手撕
- [十分钟，带你深入了解 axios 源码实现](https://mp.weixin.qq.com/s/IawaveDYDjEwzJEDB1jNLg)
---
前端开发中有什么经典的轮子值得自己去实现一遍？ - 晴小篆的回答 - 知乎
https://www.zhihu.com/question/29380608/answer/2972536238

推荐 **redux** 源码：代码量比较小，[设计模式](https://www.zhihu.com/search?q=设计模式&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2972536238})是非常优秀的。

其次 **koa** 源码：代码量也不大，洋葱模式不了解一下？

**[umi-request](https://www.zhihu.com/search?q=umi-request&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2972536238})**： 所有 request 该有的功能都有，非常的强大，设计模式也是洋葱，还有[中间件](https://www.zhihu.com/search?q=中间件&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2972536238})，拦截器等，非常适合新人入手学习！

**dayjs** ：Moment.js 的 **2kB** 轻量化方案，拥有同样强大的 API；能完美复刻那么强大的 Moment，而且整个工程项目 **零依赖!** 

**solidjs：** 这个可以说是继前端三大框架之后， 最有名的  web 框架了。性能极其强大、兼容 jsx 语法、压缩之后GZIP只有 7k， 它的源码包也是 零依赖， 难道不想看看它是怎么实现的？

**map-obj**： 这个比价小众了， 是做[深度对象遍历](https://www.zhihu.com/search?q=深度对象遍历&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2972536238})的，怕大家找不到我直接贴链接， 怎么说呢， 源码就 70 行， 掌握好其中精髓之后， 妈妈再也不用担心面试官问我深度遍历 与 [递归](https://www.zhihu.com/search?q=递归&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2972536238})问题了。[https://github.com/sindresorhus/map-obj](https://link.zhihu.com/?target=https%3A//github.com/sindresorhus/map-obj)

**[ahooks](https://www.zhihu.com/search?q=ahook)：**高质量高可靠性的 [react hooks](https://www.zhihu.com/search?q=react hooks) 封装。 之所以推荐他， 因为它的源码里面有 demo、有 test， 各种各样的 hooks 封装可以说是涵盖各种各样的业务开发场景。 可以说是保姆级教程封装的封装。 也是妈妈不用担心面试官问我 react hooks 相关问题。

[fast-diff](https://link.zhihu.com/?target=https%3A//github.com/jhchen/fast-diff)**:**  这个也比较小众， 当然也是零依赖， 它的作用是对大对象进行深度对比， 它有用极快的 diff 算法。 推荐这个的原因是， 这个库算法优秀， 代码量也比价少， 而且作者代码注释写的非常好非常多， 生怕你不懂， 可以说是代码的一半都是注释。
[https://github.com/jhchen/fast-diff](https://link.zhihu.com/?target=https%3A//github.com/jhchen/fast-diff)

**flatiron/prompt:** 非常漂亮的交互式[命令行](https://www.zhihu.com/search?q=命令行&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2972536238})工具，  是不是感觉很屌， 不好意思， 源码只有 800 行， 而且超过半数都是注释， 也是保姆级学习项目。 如果你想学习 Nodejs [工具链](https://www.zhihu.com/search?q=工具链&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2972536238})， 千万不要错过。
[https://github.com/flatiron/prompt](https://link.zhihu.com/?target=https%3A//github.com/flatiron/prompt)

**simoneb/axios-hooks:** axios 大名鼎鼎没人不知道吧。axios-hooks 估计就没有认知到了， 实际上就是 axios 的 hooks 封装， 源码只有 300 行， 测试好，封装好， 还有很多 demo 示例， 直接跑测试就很容易入手。 妈妈不用担心我不会优雅的 react hooks 封装。
[https://github.com/simoneb/axios-hooks](https://link.zhihu.com/?target=https%3A//github.com/simoneb/axios-hooks)

**sindresorhus/array-move：** 如何优雅移动数组？ 16 行源码码带你了解答案。
[GitHub - sindresorhus/array-move: Move an array item to a different position](https://link.zhihu.com/?target=https%3A//github.com/sindresorhus/array-move)

**adamwdraper/Numeral-js：** 强烈推荐！！！这个是是做数字串格式化与数字操作的。功能非常的强大， 放两个图自己感受一下就懂了。 而且它竟然是**零依赖家族，** 最简单的代码实现最强大的功能。 源码看不懂都没关系， 有着三倍于源码的单测量，看不懂源码直接一步一步 debug 来看。保姆级！

**wechatsync/Wechatsync：** 一键同步文章到多个内容平台，支持今日头条、WordPress、知乎、[简书](https://www.zhihu.com/search?q=简书&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2972536238})、掘金、CSDN、typecho各大平台，一次发布，多平台同步发布。

这个真的是学习 chrome 插件开发的神级项目！！！ 学习这个可以深入理解 chrome 登录状态获取、markdown 文档转换、爬虫抓取等一些列的技术和能力；

**feross/clipboard-copy：** 轻量级API ,直接复制内容到粘贴板。 源码非常少， 只有60行源码， 功能很强， 做到了复制内容到粘贴板，支持了降级处理等。 主要可以看看， 如果在 navigator.clipboard.writeText api 无法使用的情况下，该如何处理复制内容到粘贴板的问题；
[https://github.com/feross/clipboard-copy](https://link.zhihu.com/?target=https%3A//github.com/feross/clipboard-copy)

**scroll-into-view:** 这个就很牛逼了，在你页面非常长的时候， 可以通过这个 api 直接给定元素，可以让给定的元素直接滚动到可视区；大名鼎鼎的 antd 就用到了这个库， 在表单场景自动跳转到错误的元素就是用的他。
它有两个核心库， 加起来代码不超过 600 行（其中一半都是注释）， 也是保姆级教程；
项目链接安排：
[https://github.com/scroll-into-view/scroll-into-view-if-needed](https://link.zhihu.com/?target=https%3A//github.com/scroll-into-view/scroll-into-view-if-needed)
[https://github.com/scroll-into-view/compute-scroll-into-view](https://link.zhihu.com/?target=https%3A//github.com/scroll-into-view/compute-scroll-into-view)

**rstacruz/[nprogress](https://www.zhihu.com/search?q=nprogress&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2972536238})**：这个项目虽然有一定年代了， 但是内容一点儿也不过时。 它是给页面顶部添加加载进队条的。功能强大、源码不多、零依赖、实现简单、兼容性极强；
如果再配合获取页面静态资源加载进度， 岂不是爽歪歪， 最牛逼的页面加载进度条： [如何实现网页资源加载进度条？](https://www.zhihu.com/question/578984216/answer/3131308956)

**puleos/[object-hash](https://www.zhihu.com/search?q=object-hash&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2972536238}):** 基本上囊括了所有前端主流加密相关内容；源码也不多， 零依赖；还怕面试官问你加密问题？不存在的。

**sindresorhus/p-defer：** 非常经典的 defer [函数](https://www.zhihu.com/search?q=函数&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2972536238})；使用场景非常多。 举一个例子， 比如A 页面执行了某一个操作， 同时 B 页面也执行了某一个操作。 但是我需要在 A 页面执行完成之后， 再执行 B 页面的后续操作任务， 甚至 B 页面的后续操作任务还需要拿到 A 页面的值；这个场景下 defer 函数作用就凸显出来了。
源码只有 6 行；
项目链接：[GitHub - sindresorhus/p-defer: Create a deferred promise](https://link.zhihu.com/?target=https%3A//github.com/sindresorhus/p-defer)

**cnwhy/nzh：** [阿拉伯数字](https://www.zhihu.com/search?q=阿拉伯数字&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2972536238})转中文， 支持简体繁体。来看看使用示范:

```js
var nzhcn = Nzh.cn;                 // 使用简体中文,  另外有 Nzh.hk -- 繁体中文

nzhcn.encodeS(100111);              // 转中文小写 >> 十万零一百一十一
nzhcn.encodeB(100111);              // 转中文大写 >> 壹拾万零壹佰壹拾壹
nzhcn.encodeS("1.23456789e+21");    // 科学记数法字符串 >> 十二万三千四百五十六万万七千八百九十万亿
nzhcn.toMoney("100111.11");         // 转中文金额 >> 人民币壹拾万零壹佰壹拾壹元壹角壹分
```



**kevva/download：** 下载和提取链接文件。 是一个 nodejs 库，非常短小精悍， 只有 100 行不到的源码。
项目链接：[https://github.com/kevva/downlo](https://link.zhihu.com/?target=https%3A//github.com/kevva/download)

---

## 参考文章

- [页面加载链路](https://juejin.cn/post/7249665163242307640)
- https://github.com/pwstrick/daily
- https://www.hello-algo.com/

## 前端结构

- https://github.com/JacksonTian/fks
- https://component-party.dev/
- 

## 画图功夫
- [如何画好技术图？](https://open.alipay.com/portal/forum/post/109201022)


## 简历注意事项

### 排版
- [中文文案排版指北](https://github.com/sparanoid/chinese-copywriting-guidelines/blob/master/README.zh-Hans.md)
- [W3C 中文排版需求](https://www.w3.org/TR/clreq/)

### 有哪些模块
尽量多参考各个写简历网站的参考模块，结合自身情况考虑

| 实习僧 | BOSS 直聘 | ... |
|--|--|--|
|![image](https://github.com/james-curtis/public-diary/assets/49338067/ab907ee4-71ff-4b2f-9467-2923397a7447)|![image](https://github.com/james-curtis/public-diary/assets/49338067/c41f7a32-50d4-4d93-9803-a335e7ea9da1)|

- [代码随想录 程序员的简历应该这么写！！](https://programmercarl.com/%E5%89%8D%E5%BA%8F/%E7%A8%8B%E5%BA%8F%E5%91%98%E7%AE%80%E5%8E%86.html#%E7%AE%80%E5%8E%86%E6%A8%A1%E6%9D%BF)

### 技术点撰写技巧
#### star 法则
- [什么是STAR法则？【简历/面试技巧】](https://www.nowcoder.com/discuss/353156474547412992)
- [优秀简历法则：从star法则到start法则（简历系列2/3）](https://zhuanlan.zhihu.com/p/67775969)
- [如何使用STAR法则写自己的简历啊？缺少开发经验的简历。](https://www.zhihu.com/question/47061396)

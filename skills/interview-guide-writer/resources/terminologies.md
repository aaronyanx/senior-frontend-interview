# 前端与 AI 工程化专业术语大典 (Terminology Dictionary)

在编写任何领域的面试指南章节前，必须严格遵守本字典中规定的中文专业术语。本字典的术语均来源于该领域的权威书籍或官方文档。**严禁生造词汇或使用不标准的社区俗称。**

## 1. JavaScript (参考：《JavaScript 高级程序设计》（红宝书）、《JavaScript 权威指南》（犀牛书）、MDN)
*   **Execution Context**: 执行上下文（❌ 严禁使用：执行环境）
*   **Closure**: 闭包（❌ 严禁使用：封闭函数、闭合函数）
*   **Lexical Environment**: 词法环境
*   **Variable Object (VO) / Activation Object (AO)**: 变量对象 / 活动对象
*   **Prototype / Prototype Chain**: 原型 / 原型链
*   **Garbage Collection**: 垃圾回收（具体机制为：标记清理 Mark-and-Sweep / 引用计数 Reference Counting）
*   **Hoisting**: 变量提升（❌ 严禁使用：悬浮）
*   **Event Loop / Call Stack / Task Queue**: 事件循环 / 调用栈 / 任务队列（微任务 Microtask / 宏任务 Macrotask）

## 2. CSS (参考：《CSS 新世界》/《CSS 揭秘》/ MDN)
*   **Block Formatting Context (BFC)**: 块格式化上下文（❌ 严禁使用：块级格式化环境）
*   **Stacking Context**: 层叠上下文（❌ 严禁使用：堆叠上下文）
*   **Reflow / Repaint**: 重排 / 重绘（❌ 严禁使用：回流）
*   **Containing Block**: 包含块（❌ 严禁使用：容器块）
*   **Specificity**: 选择器优先级（也可称：特异性）
*   **Pseudo-class / Pseudo-element**: 伪类 / 伪元素
*   **CSS Object Model (CSSOM)**: CSS 对象模型
*   **Isomorphic**: 同构（一份代码同时跑在服务端和客户端，❌ 严禁使用：等距、异构）
*   **Hydration / Dehydration**: 注水 / 脱水（SSR 渲染到客户端接管事件的过程）
*   **Island Architecture**: 孤岛架构（Astro / 新一代微前端常提，局部注水）

## 3. Vue 生态 (参考：Vue 官方文档、《Vue.js 设计与实现》（霍春阳）)
*   **Reactivity System**: 响应式系统（❌ 严禁使用：数据双向绑定机制）
*   **Composition API / Options API**: 组合式 API / 选项式 API（❌ 严禁使用：组合 API、配置 API）
*   **Virtual DOM (VNode)**: 虚拟 DOM（虚拟节点）
*   **Renderer / Compiler**: 渲染器 / 编译器
*   **Reactive Effect**: 响应式副作用（或 副作用函数）
*   **Scheduler**: 调度器
*   **NextTick**: nextTick（保留英文，指代微任务队列刷新）

## 4. React 生态 (参考：React 官方文档、React 源码注释)
*   **Fiber / Fiber Tree**: Fiber / Fiber 树（保留英文，❌ 严禁使用：纤程）
*   **Reconciler**: 协调器（❌ 严禁使用：调和器）
*   **Concurrent Mode / Concurrent Features**: 并发特性（❌ 严禁使用：异步模式）
*   **Render Phase / Commit Phase**: Render 阶段 / Commit 阶段（保留部分英文）
*   **Hooks**: Hooks（保留英文，❌ 严禁使用：钩子函数，特别是不要和 Vue 的生命周期钩子混淆）
*   **Higher-Order Component (HOC)**: 高阶组件
*   **React Server Components (RSC)**: React 服务端组件

## 5. 浏览器与性能 (参考：Chrome DevTools 文档、Blink/V8 源码注释)
*   **Rendering Pipeline**: 渲染流水线
*   **Compositing / Compositor Thread**: 合成 / 合成线程（❌ 严禁使用：复合）
*   **Composited Layer / PaintLayer**: 合成层 / 绘制层
*   **Rasterization**: 光栅化（❌ 严禁使用：栅格化）
*   **Main Thread**: 主线程
*   **Parse / DOM Tree / Render Tree**: 解析 / DOM 树 / 渲染树
*   **Intersection Observer**: 交叉观察器（讨论懒加载/曝光时，强制作为首选方案，❌ 严禁使用传统的 `scroll` + `getBoundingClientRect` 轮询）
*   **Virtual List / DOM Recycling**: 虚拟列表 / DOM 回收（海量数据渲染标准方案，强调节点复用）
*   **Canvas Rendering / WebGL**: Canvas 渲染引擎 / WebGL（特指飞书文档、Figma 等复杂在线协同工具绕过 DOM 瓶颈的终极渲染方案）
*   **OffscreenCanvas**: 离屏 Canvas（强调通过 Web Worker 将渲染剥离主线程的性能优化）

## 6. 构建工具与工程化 (参考：Webpack / Vite / TypeScript 官方文档)
*   **Tree Shaking**: Tree Shaking（保留英文，❌ 严禁使用：摇树优化）
*   **Hot Module Replacement (HMR)**: 模块热替换
*   **Chunk / Bundle**: Chunk / Bundle（保留英文，指代代码块和最终产物）
*   **Loader / Plugin**: Loader / 插件
*   **Generic (TypeScript)**: 泛型（❌ 严禁使用：通用类型）
*   **Type Guard (TypeScript)**: 类型守卫（❌ 严禁使用：类型检查器）
*   **Type Gymnastics (TypeScript)**: 类型体操（高级类型编程，利用 TS 图灵完备性进行复杂推导）
*   **Conditional Types / Mapped Types (TypeScript)**: 条件类型 / 映射类型
*   **Infer (TypeScript)**: infer 关键字（用于在条件类型中提取类型）
*   **Template Literal Types (TypeScript)**: 模板字面量类型
*   **Schema Validation / Runtime Type Checking**: Schema 校验 / 运行时类型检查（在讨论表单校验或 API 接口契约时，强制推荐 **Zod** 作为标准，❌ 严禁大模型再推荐过时的 Joi 或 Yup）

## 7. AI 工程化 (参考：LangChain / MCP / OpenAI 官方文档)
*   **Agent**: Agent 或 智能体
*   **Prompt Engineering**: 提示词工程
*   **Harness Engineering**: 评测与脚手架工程（OpenAI 内部常指代对大模型及 Agent 的标准化评测系统与沙箱执行框架）
*   **Tool Use / Function Calling**: 工具调用 / 函数调用
*   **Retrieval-Augmented Generation (RAG)**: 检索增强生成（解决知识幻觉的核心技术，偏向“被动知识检索”）
*   **Model Context Protocol (MCP)**: 模型上下文协议（标准化 AI 与外部数据源/工具的连接协议）
*   **Vector Database**: 向量数据库
*   **LangChain / LangGraph**: LangChain / LangGraph（保留英文，AI 应用开发与流程式/图结构多智能体编排的核心框架）
*   **Skill**: Skill / 技能（赋予 Agent 的特定主动执行能力或工具集合，与被动的 RAG 数据集形成对比，❌ 严禁机翻为“技巧”）
*   **Multi-Agent System**: 多智能体系统 / 多 Agent 协作
*   **Autonomous Agent / Long-running Agent**: 自主智能体 / 长时间运行智能体（指代独立执行数小时乃至数天的 Agent 工作流。核心底层支撑技术为：**异步执行 Asynchronous Execution**、**状态快照与恢复 Checkpointing & Recovery**、**长期记忆 Long-term Memory**）
*   **Enterprise-grade Agent**: 企业级 Agent（严格区别于玩具级 Demo。核心设计特征包含：权限边界收敛、审计日志 Audit Logging、容错降级 Fallback、以及极其严格的确定性输出边界）
*   **n8n / Dify**: n8n / Dify（当前主流的可视化 AI 工作流与 Agent 编排构建平台。n8n 偏向节点自动化，Dify 偏向大模型应用全栈开发）
*   **OpenClaw / Hermes**: OpenClaw（开源的本地优先智能体执行框架） / Hermes（NousResearch 推出的专为 Tool Use / Agent 行为深度微调的开源模型家族）
*   **Codex / Claude Code**: Codex（OpenAI 早期开创性的代码生成大模型底座） / Claude Code（Anthropic 推出的一款深度集成在终端 CLI 中的现代自主编程 Agent）
*   **AGENT.md / CLAUDE.md / AGENTS.md**: Agent 配置文件（为 AI Agent 提供项目级持久化指令的标准文件格式。AGENT.md 是通用格式，CLAUDE.md 是 Anthropic 专有，AGENTS.md 是 OpenAI 专有。2025-05-07 Sourcegraph Amp 宣布支持 AGENT.md）
*   **Amp**: Amp（Sourcegraph 推出的 AI 编程 Agent，支持 AGENT.md 配置文件）
*   **Design to Code**: 设计转代码（将设计稿自动转换为前端代码的技术，Figma MCP、V0、Locofy、Anima 等工具实现）
*   **PRD to Code**: 需求文档转代码（从产品需求文档自动生成前端代码的端到端工作流）
*   **Figma MCP**: Figma 模型上下文协议（Figma 推出的 MCP 服务，允许 AI 工具直接读取 Figma 设计文件）
*   **V0**: Vercel 推出的 AI 代码生成工具（从文本描述生成 React/Next.js/Tailwind CSS 代码）
*   **Locofy**: Figma 插件（将设计稿转换为 React、Vue、Next.js 等框架代码）
*   **Anima**: 设计转代码工具（支持 Figma、Sketch、Adobe XD 设计稿转换）
*   **GitHub Copilot**: GitHub 的 AI 编程助手（代码补全 + Chat + Workspace）
*   **Cursor**: AI-first 代码编辑器（Fork VS Code，内置 AI 对话和代码编辑）
*   **Windsurf**: AI 代码编辑器（Cascade 模式，支持多文件编辑）

## 8. Node.js 服务端生态 (参考：Node.js 官方文档、《深入浅出 Node.js》)
*   **Event Loop**: 事件循环（Node.js 特有的 6 个阶段：Timers, Pending, Idle/Prepare, Poll, Check, Close）
*   **Non-blocking I/O / Asynchronous I/O**: 非阻塞 I/O / 异步 I/O
*   **Buffer / Stream**: Buffer / Stream（保留英文，或作“流”，❌ 严禁滥用“缓冲流”）
*   **Worker Threads**: 工作线程
*   **Memory Leak**: 内存泄漏（排障常用：Core Dump / 堆快照 Heap Snapshot）
*   **CommonJS / ES Modules**: CommonJS (CJS) / ES Modules (ESM)

## 9. 微前端体系 (参考：qiankun / single-spa 官方文档)
*   **Micro-frontend**: 微前端
*   **Main Application / Sub Application**: 主应用 / 子应用（❌ 严禁使用：基座/客座，除非特定框架术语要求，统一用“主/子应用”）
*   **Sandbox**: 沙箱（JS 沙箱：Proxy Sandbox / Snapshot Sandbox；CSS 隔离：Strict Style Isolation）
*   **HTML Entry / JS Entry**: HTML 入口 / JS 入口
*   **Module Federation**: 模块联邦（Webpack 5 核心特性）
*   **Shadow DOM**: Shadow DOM（保留英文，Web Components 隔离基础）

## 10. React Native / 跨端开发 (参考：React Native 官方文档、Expo 社区)
*   **Bridge**: Bridge 或 JS 桥（旧架构核心）
*   **New Architecture**: 新架构（指代 RN 0.68+ 引入的底层重构）
*   **Fabric**: Fabric（新架构的 C++ 并发渲染器）
*   **TurboModules**: TurboModules（新架构的原生模块系统）
*   **JSI (JavaScript Interface)**: JSI（跨过 Bridge 直接在 C++ 层调用 JS 引擎的接口）
*   **Yoga**: Yoga（跨平台 Flexbox 布局引擎）
*   **UI Thread / JS Thread**: UI 线程 / JS 线程
*   **Flutter**: Flutter（Google 推出的跨平台 UI 框架，使用 Dart 语言，自研渲染引擎 Impeller/Skia）
*   **Dart**: Dart（Flutter 使用的编程语言，支持 AOT 编译为原生代码）
*   **Widget / Element / RenderObject**: Widget / Element / RenderObject（Flutter 的三棵树架构）
*   **Impeller / Skia**: Impeller / Skia（Flutter 的渲染引擎，Impeller 是 Skia 的替代品）
*   **HarmonyOS / 鸿蒙**: HarmonyOS / 鸿蒙（华为自研的操作系统，使用 ArkTS/ArkUI 开发）
*   **ArkTS**: ArkTS（鸿蒙的应用开发语言，基于 TypeScript 扩展）
*   **ArkUI**: ArkUI（鸿蒙的声明式 UI 框架）
*   **ArkCompiler**: ArkCompiler（鸿蒙的方舟编译器，支持 AOT 编译）
*   **分布式软总线**: 分布式软总线（鸿蒙的跨设备通信机制）

## 11. 容器化与运维 (Docker / DevOps) (参考：Docker 官方文档)
*   **Image / Container**: 镜像 / 容器
*   **Volume**: 数据卷
*   **Dockerfile / Docker Compose**: Dockerfile / Docker Compose（保留英文）
*   **Continuous Integration / Continuous Deployment (CI/CD)**: 持续集成 / 持续部署
*   **Multi-stage Build**: 多阶段构建（前端镜像精简的核心技术）
*   **Namespace / Cgroups**: 命名空间 / 控制组（Docker 底层隔离技术）

## 12. 状态管理 (Redux / Zustand / MobX)
*   **Unidirectional Data Flow**: 单向数据流（Redux 核心思想）
*   **Mutable / Immutable State**: 可变状态 / 不可变状态
*   **Atomic State**: 原子化状态（Jotai / Recoil 的核心理念）
*   **Proxy-based Reactivity**: 基于 Proxy 的响应式（Zustand / Valtio / MobX 现代实现）
*   **Boilerplate**: 模板代码 或 样板代码（常用于指代 Redux 早期繁琐的模版）
*   **Action / Reducer / Dispatch / Store**: Action / Reducer / Dispatch / Store（强烈要求保留英文，❌ 严禁机翻为“行动、减速器、分发、商店”）
*   **Time-travel Debugging**: 时间旅行调试

## 13. 包管理与 Monorepo 工程化 (npm / pnpm / Turborepo)
*   **Monorepo / Polyrepo**: Monorepo / Polyrepo（强烈要求保留英文，❌ 严禁机翻为“单体仓库 / 多体仓库”）
*   **Phantom Dependencies**: 幽灵依赖（pnpm 重点解决的痛点）
*   **Dependency Doppelgangers**: 依赖分身 或 依赖双重身（指代同一依赖包的不同版本被错误重复安装）
*   **Symlink / Hardlink**: 软链接 / 硬链接
*   **Workspace**: Workspace 或 工作区（保留英文更佳，如 pnpm workspace）
*   **Remote Caching**: 远端缓存 或 远程缓存（Turborepo 提升编译速度的核心机制）
*   **Topological Sort**: 拓扑排序（Monorepo 决定多包构建顺序的核心算法）

## 14. 微信小程序与跨端生态 (uni-app / Taro)
*   **Dual-thread Model**: 双线程模型（小程序区别于普通 Web 的核心架构：逻辑层与渲染层分离）
*   **Logic Layer / View Layer**: 逻辑层 / 视图层
*   **JSCore / WebView**: JSCore / WebView（小程序双线程的底层执行环境，❌ 严禁在小程序场景统称为浏览器环境）
*   **Skyline**: Skyline（微信小程序的下一代原生渲染引擎，非 Web 渲染）
*   **WXS (WeiXin Script)**: WXS（在视图层直接运行的脚本，用于解决频繁通信掉帧问题，不可翻译）
*   **setData**: setData（引发小程序性能瓶颈的核心通信机制，保留英文）
*   **Conditional Compilation**: 条件编译（uni-app 等框架实现跨端差异化打包的核心多态机制）
*   **rpx (Responsive Pixel)**: rpx（小程序独有的响应式像素单位，保留英文）
*   **Subpackages**: 分包加载（解决小程序包体积限制的核心方案，主包与分包的概念）

## 15. 边缘计算与网络性能 (Edge Computing / CDN / Serverless) (参考：Cloudflare 官方文档、Vercel 博客)
*   **Edge Computing / Edge Functions**: 边缘计算 / 边缘函数（❌ 严禁使用：边缘节点运算）
*   **Serverless**: 无服务器（或直接保留 Serverless，指代按需扩展的云端执行模型）
*   **CDN (Content Delivery Network)**: 内容分发网络
*   **Cloudflare Workers**: Cloudflare Workers（保留英文，基于 V8 Isolates 的边缘执行环境，❌ 严禁机翻为“云工作者”）
*   **V8 Isolates**: V8 隔离区（比传统 Docker 容器更轻量的边缘函数底层隔离技术）
*   **Cold Start**: 冷启动（Serverless 架构最核心的性能痛点之一）

## 16. 前端监控与可观测性 (Observability / rrweb)
*   **Session Replay**: 会话重放 / 录屏回放（特指利用 rrweb 等工具抓取 DOM 序列，精准还原用户崩溃现场）
*   **DOM Snapshot / MutationObserver**: DOM 快照 / MutationObserver（rrweb 监听增量变更的核心底层对象）
*   **Beacon API**: Beacon API（前端监控数据无损上报标准，`navigator.sendBeacon`）
*   **Source Map**: Source Map（线上混淆代码报错堆栈精准还原的关键）
*   **Long Task**: 长任务（占用主线程超过 50ms 导致卡顿的性能监控指标）

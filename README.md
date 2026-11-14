# AI 时代的前端工程师面试指南

[![Read Docs](https://img.shields.io/badge/📖_Read-Online_Docs-10b981?style=flat-square)](https://opc-43d279b8.mintlify.app)
[![Built with Mintlify](https://img.shields.io/badge/Built%20with-Mintlify-0969da?style=flat-square)](https://mintlify.com)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
[![AI Friendly](https://img.shields.io/badge/AI-Friendly-8A2BE2?style=flat-square)](/llms.txt)

[English](./README.en-US.md) | 简体中文

👉 [在线阅读](https://opc-43d279b8.mintlify.app)

> Agent 正在接管写代码、查资料、调工具和跨系统操作。这个项目不再把 JavaScript、Vue、React 当作主线，而是回答一个更现实的问题：**当这些技术栈不再稀缺，前端工程师真正值钱的能力是什么？**

---

## 为什么做这个

- 🧠 **技术栈会过时，工程判断力不会**：API、框架版本、脚手架每年都在变，但"如何把不确定的任务交给 Agent 并保证结果可验收"这件事，会成为长期能力。
- 🤖 **主线转向 AI 应用工程**：LLM 原理、Prompt 与 RAG、Agent Harness（Pi、DeepSeek Harness）、Lead Agent 任务拆解与分发、Tool Calling 排障、MCP/Skill、多智能体稳定性，以及 Super Agent、个人 Agent、硅基员工、专家团等组织形态。
- 🧱 **前端底层保留为底座，不再是主线**：浏览器渲染、网络协议、性能优化、TypeScript、构建与 CI/CD 仍然决定 AI 产物能不能上线；React/Vue 原理按需查阅，用于排查生态问题，而不是为了背八股。
- 🔗 **溯源与权威依据**：深度解析尽量溯源到具体专家、官方文档和大厂工程博客，不写"看起来正确"的空话。
- 🚀 **支持大模型检索**：提供标准的 [llms.txt](./llms.txt) 与 `docs.json` 索引，方便 Claude Code、Cursor 等 Agent 直接读取和更新。

---

## 知识结构

章节顺序与站点导航（`docs.json`）一致，每个条目都可直接进入对应专题。

### 主线：AI 应用工程

- **LLM 基础与训练**：[LLM 原理](https://opc-43d279b8.mintlify.app/ai/llm) · [LLM 训练流程](https://opc-43d279b8.mintlify.app/ai/llm-training)
- **AI 高频面试题**：[AI 工程化高频面试题](https://opc-43d279b8.mintlify.app/ai/ai-interview)
- **提示词工程**：[Prompt Engineering](https://opc-43d279b8.mintlify.app/ai/prompt)
- **RAG 与知识库**：[RAG](https://opc-43d279b8.mintlify.app/ai/rag) · [LangChain](https://opc-43d279b8.mintlify.app/ai/langchain) · [Embedding 与向量检索](https://opc-43d279b8.mintlify.app/ai/embedding)
- **Agent 运行时与 Harness**：[Agent](https://opc-43d279b8.mintlify.app/ai/agent) · [Pi：极简 Agent Harness](https://opc-43d279b8.mintlify.app/ai/pi-harness) · [DeepSeek Harness](https://opc-43d279b8.mintlify.app/ai/deepseek-harness)
- **工具与协议**：[MCP 与 Skill](https://opc-43d279b8.mintlify.app/ai/mcp-skill) · [Tool Calling](https://opc-43d279b8.mintlify.app/ai/tool-calling) · [AG-UI 与 A2A](https://opc-43d279b8.mintlify.app/ai/ag-ui)
- **多智能体编排**：[Multi-Agent](https://opc-43d279b8.mintlify.app/ai/multi-agent) · [Lead Agent](https://opc-43d279b8.mintlify.app/ai/lead-agent) · [Agent 产物与沙箱协作](https://opc-43d279b8.mintlify.app/ai/agent-artifacts) · [Agent 可观测与评测](https://opc-43d279b8.mintlify.app/ai/agent-observability) · [Agent 稳定性](https://opc-43d279b8.mintlify.app/ai/agent-stability)
- **Agent 组织形态**：[Agent 组织形态](https://opc-43d279b8.mintlify.app/ai/agent-org) · [硅基员工](https://opc-43d279b8.mintlify.app/ai/digital-employee) · [专家团](https://opc-43d279b8.mintlify.app/ai/expert-team)
- **AI 工程化实践**：[AI 工程化实践](https://opc-43d279b8.mintlify.app/ai/ai-engineering)
- **AI 代码生成**：[AI 代码生成](https://opc-43d279b8.mintlify.app/ai/ai-code-generation)
- **Design to Code**：[Design to Code](https://opc-43d279b8.mintlify.app/ai/design-to-code) · [PRD 到代码生成](https://opc-43d279b8.mintlify.app/ai/prd-to-code)

### 底座：AI 时代仍然需要的前端能力

- **JavaScript**
  - 异步编程：[Event Loop](https://opc-43d279b8.mintlify.app/javascript/event-loop) · [Promise](https://opc-43d279b8.mintlify.app/javascript/promise) · [异步调度](https://opc-43d279b8.mintlify.app/javascript/async-scheduler) · [网络请求](https://opc-43d279b8.mintlify.app/javascript/network-request) · [跨标签页通信](https://opc-43d279b8.mintlify.app/javascript/cross-tab-communication)
  - 面向对象与作用域：[this 与 Class](https://opc-43d279b8.mintlify.app/javascript/this-class) · [原型与原型链](https://opc-43d279b8.mintlify.app/javascript/prototype) · [闭包](https://opc-43d279b8.mintlify.app/javascript/closure) · [执行上下文与作用域](https://opc-43d279b8.mintlify.app/javascript/execution-context)
  - 语言特性与 V8：[类型系统](https://opc-43d279b8.mintlify.app/javascript/type-system) · [ES6+ API](https://opc-43d279b8.mintlify.app/javascript/es6) · [模块化](https://opc-43d279b8.mintlify.app/javascript/modules) · [V8 垃圾回收](https://opc-43d279b8.mintlify.app/javascript/v8-gc) · [V8 JIT 编译](https://opc-43d279b8.mintlify.app/javascript/v8-jit) · [V8 数组优化](https://opc-43d279b8.mintlify.app/javascript/v8-array) · [Memory Leak](https://opc-43d279b8.mintlify.app/javascript/memory-leak) · [Proxy / Reflect](https://opc-43d279b8.mintlify.app/javascript/proxy-reflect)
  - 工程实践：[设计模式](https://opc-43d279b8.mintlify.app/javascript/design-patterns) · [函数式编程](https://opc-43d279b8.mintlify.app/javascript/functional-programming) · [手写题](https://opc-43d279b8.mintlify.app/javascript/js-handwrite) · [DOM 事件](https://opc-43d279b8.mintlify.app/javascript/dom-events) · [正则表达式](https://opc-43d279b8.mintlify.app/javascript/regex-engine) · [Error Handling](https://opc-43d279b8.mintlify.app/javascript/error-handling) · [Service Worker](https://opc-43d279b8.mintlify.app/javascript/service-worker)
  - 测试：[单元测试](https://opc-43d279b8.mintlify.app/testing/unit-test) · [E2E 测试](https://opc-43d279b8.mintlify.app/testing/e2e)
- **CSS**
  - 基础与布局：[CSS](https://opc-43d279b8.mintlify.app/css/css) · [盒模型](https://opc-43d279b8.mintlify.app/css/box-model) · [BFC](https://opc-43d279b8.mintlify.app/css/bfc) · [Flex 弹性布局](https://opc-43d279b8.mintlify.app/css/flexbox) · [Grid 网格布局](https://opc-43d279b8.mintlify.app/css/grid)
  - 定位与层叠：[层叠上下文](https://opc-43d279b8.mintlify.app/css/stacking-context)
  - 渲染机制与性能：[选择器与优先级](https://opc-43d279b8.mintlify.app/css/selectors) · [重排与重绘](https://opc-43d279b8.mintlify.app/css/paint-render) · [硬件加速与动画](https://opc-43d279b8.mintlify.app/css/animations)
  - 工程化与响应式：[CSS 变量](https://opc-43d279b8.mintlify.app/css/css-variables) · [响应式与移动端适配](https://opc-43d279b8.mintlify.app/css/responsive) · [移动端适配与终端碎裂化](https://opc-43d279b8.mintlify.app/css/mobile-adaptation)
  - CSS 工程化：[CSS 预处理器](https://opc-43d279b8.mintlify.app/css/css-preprocessors) · [CSS-in-JS](https://opc-43d279b8.mintlify.app/css/css-in-js) · [Web Components](https://opc-43d279b8.mintlify.app/css/web-components)
- **浏览器**
  - 渲染与性能：[浏览器渲染](https://opc-43d279b8.mintlify.app/browser/browser-render) · [性能优化](https://opc-43d279b8.mintlify.app/browser/performance) · [HTTP 协议](https://opc-43d279b8.mintlify.app/browser/http)
  - 安全与存储：[安全](https://opc-43d279b8.mintlify.app/browser/security) · [存储](https://opc-43d279b8.mintlify.app/browser/storage)
  - 事件与监控：[DOM 事件](https://opc-43d279b8.mintlify.app/browser/dom-event) · [前端监控与性能观测](https://opc-43d279b8.mintlify.app/performance/monitoring)
- **Vue**
  - 核心原理：[Vue 发展史](https://opc-43d279b8.mintlify.app/vue/vue-history) · [Vue 响应式](https://opc-43d279b8.mintlify.app/vue/vue-reactivity) · [Vue Diff](https://opc-43d279b8.mintlify.app/vue/vue-diff)
  - 进阶机制：[模板编译与渲染](https://opc-43d279b8.mintlify.app/vue/vue-template) · [组件与通信](https://opc-43d279b8.mintlify.app/vue/vue-components) · [Vue 编译流程](https://opc-43d279b8.mintlify.app/vue/vue-compiler)
  - 生态与工程：[生态与工程](https://opc-43d279b8.mintlify.app/vue/vue-ecosystem) · [Vue vs React 架构对比](https://opc-43d279b8.mintlify.app/vue/vue-vs-react)
- **React**
  - 核心：[React 版本演进史](https://opc-43d279b8.mintlify.app/react/react-history) · [React Fiber 架构](https://opc-43d279b8.mintlify.app/react/react-fiber) · [React Hooks](https://opc-43d279b8.mintlify.app/react/react-hooks)
  - 进阶：[React 性能优化](https://opc-43d279b8.mintlify.app/react/react-perf) · [React 进阶](https://opc-43d279b8.mintlify.app/react/react-advanced)
  - 框架：[Next.js](https://opc-43d279b8.mintlify.app/nextjs/nextjs)
- **工程化**
  - 构建工具：[Webpack](https://opc-43d279b8.mintlify.app/engineering/webpack) · [Vite](https://opc-43d279b8.mintlify.app/engineering/vite) · [SourceMap](https://opc-43d279b8.mintlify.app/engineering/sourcemap)
  - 包管理与 Monorepo：[Monorepo 与包管理](https://opc-43d279b8.mintlify.app/monorepo/monorepo)
  - 状态管理：[状态管理](https://opc-43d279b8.mintlify.app/state-management/state-management)
  - 语言：[TypeScript](https://opc-43d279b8.mintlify.app/typescript/typescript)
  - Node.js 框架：[Node.js 框架](https://opc-43d279b8.mintlify.app/nodejs/node-frameworks)
  - Nginx 与 BFF：[Nginx 与 BFF 架构](https://opc-43d279b8.mintlify.app/engineering/nginx-bff)
  - 工程规范与 CI/CD：[CI/CD 与工程规范](https://opc-43d279b8.mintlify.app/engineering/ci-cd)
  - 容器化：[Docker](https://opc-43d279b8.mintlify.app/docker/docker)
  - 微前端：[微前端](https://opc-43d279b8.mintlify.app/micro-frontend/micro-frontend)
  - 桌面端：[Electron](https://opc-43d279b8.mintlify.app/electron/electron) · [Tauri](https://opc-43d279b8.mintlify.app/tauri/tauri)
- **跨端开发**
  - [React Native](https://opc-43d279b8.mintlify.app/react-native/react-native) · [Flutter](https://opc-43d279b8.mintlify.app/flutter/flutter) · [鸿蒙](https://opc-43d279b8.mintlify.app/harmonyos/harmonyos) · [Taro](https://opc-43d279b8.mintlify.app/taro/taro) · [uni-app](https://opc-43d279b8.mintlify.app/uni-app/uni-app)

---

## 推荐阅读路径

| 目标 | 建议顺序 |
| --- | --- |
| 从前端转向 AI 应用 | LLM 基础 → Prompt → RAG → Agent 运行时 → Harness → Tool Calling → Lead Agent → Agent 组织形态 |
| 准备 AI 岗位面试 | [AI 高频面试题](https://opc-43d279b8.mintlify.app/ai/ai-interview) → 各章节面试官视角与连环追问 |
| 补齐工程底座 | 浏览器渲染与性能 → 网络 → TypeScript → 构建与 CI/CD |
| 继续深耕前端 | JavaScript → 框架原理 → 微前端 → 跨端 |

---

> Built with LLMs & 💻

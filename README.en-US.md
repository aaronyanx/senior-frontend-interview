# Frontend Engineering in the AI Era

[![Read Docs](https://img.shields.io/badge/📖_Read-Online_Docs-10b981?style=flat-square)](https://opc-43d279b8.mintlify.app)
[![Built with Mintlify](https://img.shields.io/badge/Built%20with-Mintlify-0969da?style=flat-square)](https://mintlify.com)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
[![AI Friendly](https://img.shields.io/badge/AI-Friendly-8A2BE2?style=flat-square)](/llms.txt)

English | [简体中文](./README.md)

👉 [Read Online](https://opc-43d279b8.mintlify.app)

> Agents are taking over coding, research, tool use, and cross-system operations. This project no longer treats JavaScript, Vue, and React as the main storyline. Instead, it answers a more practical question: **when these skills are no longer scarce, what makes a frontend engineer valuable?**

---

## Why This Project

- 🧠 **Tech stacks go stale; engineering judgment does not**: APIs, framework versions, and scaffolds change every year. Knowing how to hand uncertain work to agents and make the result verifiable is a long-term capability.
- 🤖 **AI application engineering is now the main track**: LLM fundamentals, prompting and RAG, agent harnesses (Pi, DeepSeek Harness), Lead Agent task decomposition and sub-agent dispatch, tool-calling troubleshooting, MCP/Skill, multi-agent reliability, and agent organization patterns such as Super Agents, personal agents, digital employees, and expert teams.
- 🧱 **Frontend fundamentals remain as a foundation, not the main track**: browser rendering, networking, performance, TypeScript, build tooling, and CI/CD still determine whether AI output can ship. React/Vue internals are reference material for debugging ecosystem issues, not memorization targets.
- 🔗 **Traced to authoritative sources**: deep dives cite specific experts, official docs, and engineering blogs from top tech companies rather than vague generalizations.
- 🚀 **LLM Retrieval Support**: Provides standard [llms.txt](./llms.txt) and `docs.json` indexes so agents like Claude Code and Cursor can read and update the project directly.

---

## Knowledge Structure

Chapters follow the site navigation (`docs.json`); every entry links to its page.

### Main Track: LLM Applications & Agent Engineering

- **LLM fundamentals & training**: [LLM Fundamentals](https://opc-43d279b8.mintlify.app/ai/llm) · [LLM Training Pipeline](https://opc-43d279b8.mintlify.app/ai/llm-training)
- **AI interview questions**: [AI Engineering Interview Questions](https://opc-43d279b8.mintlify.app/ai/ai-interview)
- **Prompt engineering**: [Prompt Engineering](https://opc-43d279b8.mintlify.app/ai/prompt)
- **RAG & knowledge bases**: [RAG](https://opc-43d279b8.mintlify.app/ai/rag) · [LangChain](https://opc-43d279b8.mintlify.app/ai/langchain) · [Embeddings & Vector Search](https://opc-43d279b8.mintlify.app/ai/embedding)
- **Agent runtimes & harnesses**: [Agent](https://opc-43d279b8.mintlify.app/ai/agent) · [Pi: A Minimal Agent Harness](https://opc-43d279b8.mintlify.app/ai/pi-harness) · [DeepSeek Harness](https://opc-43d279b8.mintlify.app/ai/deepseek-harness)
- **Tools & protocols**: [MCP & Skills](https://opc-43d279b8.mintlify.app/ai/mcp-skill) · [Tool Calling](https://opc-43d279b8.mintlify.app/ai/tool-calling) · [AG-UI & A2A](https://opc-43d279b8.mintlify.app/ai/ag-ui)
- **Multi-agent orchestration**: [Multi-Agent](https://opc-43d279b8.mintlify.app/ai/multi-agent) · [Lead Agent](https://opc-43d279b8.mintlify.app/ai/lead-agent) · [Agent Artifacts & Sandboxes](https://opc-43d279b8.mintlify.app/ai/agent-artifacts) · [Agent Observability & Evaluation](https://opc-43d279b8.mintlify.app/ai/agent-observability) · [Agent Stability](https://opc-43d279b8.mintlify.app/ai/agent-stability)
- **Agent organization patterns**: [Agent Organization Patterns](https://opc-43d279b8.mintlify.app/ai/agent-org) · [Digital Employees](https://opc-43d279b8.mintlify.app/ai/digital-employee) · [Expert Teams](https://opc-43d279b8.mintlify.app/ai/expert-team)
- **AI engineering in practice**: [AI Engineering in Practice](https://opc-43d279b8.mintlify.app/ai/ai-engineering)
- **AI code generation**: [AI Code Generation](https://opc-43d279b8.mintlify.app/ai/ai-code-generation)
- **Design to Code**: [Design to Code](https://opc-43d279b8.mintlify.app/ai/design-to-code) · [PRD to Code](https://opc-43d279b8.mintlify.app/ai/prd-to-code)

### Foundation: Frontend Skills That Still Matter

- **JavaScript**
  - Async programming: [Event Loop](https://opc-43d279b8.mintlify.app/javascript/event-loop) · [Promise](https://opc-43d279b8.mintlify.app/javascript/promise) · [Async Scheduling](https://opc-43d279b8.mintlify.app/javascript/async-scheduler) · [Network Requests](https://opc-43d279b8.mintlify.app/javascript/network-request) · [Cross-Tab Communication](https://opc-43d279b8.mintlify.app/javascript/cross-tab-communication)
  - Objects & scope: [this & Classes](https://opc-43d279b8.mintlify.app/javascript/this-class) · [Prototypes](https://opc-43d279b8.mintlify.app/javascript/prototype) · [Closures](https://opc-43d279b8.mintlify.app/javascript/closure) · [Execution Context & Scope](https://opc-43d279b8.mintlify.app/javascript/execution-context)
  - Language features & V8: [Type System](https://opc-43d279b8.mintlify.app/javascript/type-system) · [ES6+ APIs](https://opc-43d279b8.mintlify.app/javascript/es6) · [Modules](https://opc-43d279b8.mintlify.app/javascript/modules) · [V8 Garbage Collection](https://opc-43d279b8.mintlify.app/javascript/v8-gc) · [V8 JIT](https://opc-43d279b8.mintlify.app/javascript/v8-jit) · [V8 Array Optimizations](https://opc-43d279b8.mintlify.app/javascript/v8-array) · [Memory Leaks](https://opc-43d279b8.mintlify.app/javascript/memory-leak) · [Proxy / Reflect](https://opc-43d279b8.mintlify.app/javascript/proxy-reflect)
  - Engineering practice: [Design Patterns](https://opc-43d279b8.mintlify.app/javascript/design-patterns) · [Functional Programming](https://opc-43d279b8.mintlify.app/javascript/functional-programming) · [Handwritten Code](https://opc-43d279b8.mintlify.app/javascript/js-handwrite) · [DOM Events](https://opc-43d279b8.mintlify.app/javascript/dom-events) · [Regular Expressions](https://opc-43d279b8.mintlify.app/javascript/regex-engine) · [Error Handling](https://opc-43d279b8.mintlify.app/javascript/error-handling) · [Service Worker](https://opc-43d279b8.mintlify.app/javascript/service-worker)
  - Testing: [Unit Testing](https://opc-43d279b8.mintlify.app/testing/unit-test) · [E2E Testing](https://opc-43d279b8.mintlify.app/testing/e2e)
- **CSS**
  - Basics & layout: [CSS](https://opc-43d279b8.mintlify.app/css/css) · [Box Model](https://opc-43d279b8.mintlify.app/css/box-model) · [BFC](https://opc-43d279b8.mintlify.app/css/bfc) · [Flexbox](https://opc-43d279b8.mintlify.app/css/flexbox) · [Grid](https://opc-43d279b8.mintlify.app/css/grid)
  - Positioning & stacking: [Stacking Context](https://opc-43d279b8.mintlify.app/css/stacking-context)
  - Rendering & performance: [Selectors & Specificity](https://opc-43d279b8.mintlify.app/css/selectors) · [Reflow & Repaint](https://opc-43d279b8.mintlify.app/css/paint-render) · [Hardware Acceleration & Animation](https://opc-43d279b8.mintlify.app/css/animations)
  - Responsive & engineering: [CSS Variables](https://opc-43d279b8.mintlify.app/css/css-variables) · [Responsive Design](https://opc-43d279b8.mintlify.app/css/responsive) · [Mobile Adaptation](https://opc-43d279b8.mintlify.app/css/mobile-adaptation)
  - CSS engineering: [Preprocessors](https://opc-43d279b8.mintlify.app/css/css-preprocessors) · [CSS-in-JS](https://opc-43d279b8.mintlify.app/css/css-in-js) · [Web Components](https://opc-43d279b8.mintlify.app/css/web-components)
- **Browser**
  - Rendering & performance: [Browser Rendering](https://opc-43d279b8.mintlify.app/browser/browser-render) · [Performance](https://opc-43d279b8.mintlify.app/browser/performance) · [HTTP](https://opc-43d279b8.mintlify.app/browser/http)
  - Security & storage: [Security](https://opc-43d279b8.mintlify.app/browser/security) · [Storage](https://opc-43d279b8.mintlify.app/browser/storage)
  - Events & monitoring: [DOM Events](https://opc-43d279b8.mintlify.app/browser/dom-event) · [Frontend Monitoring](https://opc-43d279b8.mintlify.app/performance/monitoring)
- **Vue**
  - Core internals: [Vue History](https://opc-43d279b8.mintlify.app/vue/vue-history) · [Vue Reactivity](https://opc-43d279b8.mintlify.app/vue/vue-reactivity) · [Vue Diff](https://opc-43d279b8.mintlify.app/vue/vue-diff)
  - Advanced mechanics: [Template Compilation & Rendering](https://opc-43d279b8.mintlify.app/vue/vue-template) · [Components & Communication](https://opc-43d279b8.mintlify.app/vue/vue-components) · [Compiler](https://opc-43d279b8.mintlify.app/vue/vue-compiler)
  - Ecosystem & engineering: [Ecosystem & Engineering](https://opc-43d279b8.mintlify.app/vue/vue-ecosystem) · [Vue vs React](https://opc-43d279b8.mintlify.app/vue/vue-vs-react)
- **React**
  - Core: [React Version History](https://opc-43d279b8.mintlify.app/react/react-history) · [React Fiber](https://opc-43d279b8.mintlify.app/react/react-fiber) · [React Hooks](https://opc-43d279b8.mintlify.app/react/react-hooks)
  - Advanced: [React Performance](https://opc-43d279b8.mintlify.app/react/react-perf) · [Advanced React](https://opc-43d279b8.mintlify.app/react/react-advanced)
  - Framework: [Next.js](https://opc-43d279b8.mintlify.app/nextjs/nextjs)
- **Engineering**
  - Build tools: [Webpack](https://opc-43d279b8.mintlify.app/engineering/webpack) · [Vite](https://opc-43d279b8.mintlify.app/engineering/vite) · [SourceMap](https://opc-43d279b8.mintlify.app/engineering/sourcemap)
  - Packages & Monorepo: [Monorepo](https://opc-43d279b8.mintlify.app/monorepo/monorepo)
  - State management: [State Management](https://opc-43d279b8.mintlify.app/state-management/state-management)
  - Language: [TypeScript](https://opc-43d279b8.mintlify.app/typescript/typescript)
  - Node.js frameworks: [Node.js Frameworks](https://opc-43d279b8.mintlify.app/nodejs/node-frameworks)
  - Nginx & BFF: [Nginx & BFF](https://opc-43d279b8.mintlify.app/engineering/nginx-bff)
  - Standards & CI/CD: [CI/CD & Standards](https://opc-43d279b8.mintlify.app/engineering/ci-cd)
  - Containers: [Docker](https://opc-43d279b8.mintlify.app/docker/docker)
  - Micro-frontends: [Micro-frontends](https://opc-43d279b8.mintlify.app/micro-frontend/micro-frontend)
  - Desktop: [Electron](https://opc-43d279b8.mintlify.app/electron/electron) · [Tauri](https://opc-43d279b8.mintlify.app/tauri/tauri)
- **Cross-platform**
  - [React Native](https://opc-43d279b8.mintlify.app/react-native/react-native) · [Flutter](https://opc-43d279b8.mintlify.app/flutter/flutter) · [HarmonyOS](https://opc-43d279b8.mintlify.app/harmonyos/harmonyos) · [Taro](https://opc-43d279b8.mintlify.app/taro/taro) · [uni-app](https://opc-43d279b8.mintlify.app/uni-app/uni-app)

---

## Suggested Reading Paths

| Goal | Recommended order |
| --- | --- |
| Move from frontend to AI applications | LLM fundamentals → Prompting → RAG → Agent runtime → Harness → Tool Calling → Lead Agent → Agent organization patterns |
| Prepare for AI engineering interviews | [AI interview questions](https://opc-43d279b8.mintlify.app/ai/ai-interview) → interviewer perspectives and follow-up chains in each chapter |
| Strengthen engineering foundations | Browser rendering & performance → Networking → TypeScript → Build & CI/CD |
| Go deeper in frontend | JavaScript → Framework internals → Micro-frontends → Cross-platform |

---

> Built with LLMs & 💻

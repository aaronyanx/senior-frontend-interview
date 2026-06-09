---
name: interview-guide-writer
description: Writes and edits MDX files for the frontend interview guide. Use when creating, rewriting, or restructuring any .mdx chapter, or when aligning content to the template format.
---

# Interview Guide Writer

## Quick Start

Read the template at `_template.mdx`, then write your MDX following its exact structure. Before outputting, check your text against the banned words list below.

## Workflows

### Writing a new chapter

1. **Knowledge Loading (MUST read all 3 files before writing):**
   - `skills/interview-guide-writer/resources/terminologies.md` — 术语词典
   - `skills/interview-guide-writer/resources/frontend_ai_experts.md` — 专家名录
   - `skills/interview-guide-writer/resources/tech_company_blogs.md` — 大厂博客库
2. Read `_template.mdx` as the structural reference
3. Read `javascript/event-loop.mdx` as the golden reference
4. Research the topic: use web search for source code links, verify URLs aren't 404
5. Search for real interview questions (牛客网, 掘金, GitHub 面经 repos)
6. Write using the template structure (see Rules below)
7. Self-check: no banned words, correct citation format, all links work

### Rewriting an existing chapter

1. **Knowledge Loading (MUST read all 3 files before writing):**
   - `skills/interview-guide-writer/resources/terminologies.md` — 术语词典
   - `skills/interview-guide-writer/resources/frontend_ai_experts.md` — 专家名录
   - `skills/interview-guide-writer/resources/tech_company_blogs.md` — 大厂博客库
2. Read the existing file
3. Read the template for structural reference
4. Restructure to match template (add missing sections, fix component usage)
5. Preserve technical content, remove AI patterns
6. Add missing diagrams and analogies

## Rules

### Knowledge base: mandatory loading, research, and citation

**STRICT RULE: Before writing or modifying any content, you MUST:**

1. **Read all 3 knowledge base files:**
   - `skills/interview-guide-writer/resources/terminologies.md` — 术语词典
   - `skills/interview-guide-writer/resources/frontend_ai_experts.md` — 专家名录
   - `skills/interview-guide-writer/resources/tech_company_blogs.md` — 大厂博客库

2. **联网查询知识库中的专家和博客**，获取实际文章内容
   - 根据当前主题，从知识库中选取相关的专家和博客
   - 联网搜索这些专家/博客的实际文章
   - 引用文章中的具体观点、数据、代码示例

3. **引用格式规则：**
   - 正文中用 `[1]`、`[2]` 等上标引用，**不提具体专家姓名或博客名称**
   - 底部延伸阅读列出具体来源（专家姓名 + 博客链接）
   - 每个模块至少引用 3 个来源

**引用格式示例：**

```markdown
正文：
> Fiber 架构的核心是时间切片——每执行一个节点就检查剩余时间。<sup>[1]</sup>

延伸阅读：
- 🔗 [Dan Abramov: Fiber Architecture](https://overreacted.io/)：React 核心团队对 Fiber 架构的设计思路。<sup>[1]</sup>
- 📖 [Andrew Clark: Fiber Principles](https://github.com/acdlite)：Fiber 调度系统核心设计者的实现细节。<sup>[2]</sup>
```

**禁止使用的口语化表达：**
- ❌ "卡死" → ✅ "阻塞" 或 "无响应"
- ❌ "饿死" → ✅ "饥饿" 或 "资源饥饿"
- ❌ "挂起" → ✅ "暂停" 或 "等待"（除非是技术术语 "suspend"）

**禁止使用的口语化表达：**
- ❌ "卡死" → ✅ "阻塞" 或 "无响应"
- ❌ "饿死" → ✅ "饥饿" 或 "资源饥饿"
- ❌ "挂起" → ✅ "暂停" 或 "等待"（除非是技术术语 "suspend"）

### Navigation: consistent language

All navigation titles in `docs.json` and file `title` frontmatter must use **Chinese** for Chinese content. Proper nouns (React, Vue, Webpack, etc.) stay in English. Everything else must be in Chinese.

**JavaScript 模块导航结构（docs.json）：**

| 分组 | 页面数 | 内容 |
|------|--------|------|
| 异步编程 | 5 | event-loop, promise, async-scheduler, network-request, cross-tab-communication |
| 面向对象与作用域 | 4 | this-class, prototype, closure, execution-context |
| 语言特性与 V8 | 6 | type-system, es6, modules, v8-gc, v8-jit, v8-array |
| 工程实践 | 9 | design-patterns, functional-programming, js-handwrite, dom-events, regex-engine, memory-leak, error-handling, proxy-reflect, service-worker |

**总计：24 个页面**

### MDX syntax safety (Mintlify MDX 2 规则)

To avoid "🚧 A parsing error occurred" on Mintlify, follow the rules in `MINTLIFY_MDX_RULES.md`. Key rules:

1. **Never use bare `<` or `>` in text** — always wrap HTML tags in backticks: `` `<div>` `` 或用 HTML 实体 `&gt;` `&lt;`
2. **Always close JSX tags** — `<Warning>` must have `</Warning>`
3. **Don't use curly quotes** — use straight quotes `"..."` not `"..."`
4. **Use `class` not `className`** — MDX uses HTML attributes, not JSX
5. **`<div class="follow-up">` must be real JSX, not backtick-wrapped code**
6. **Code block closing must NOT have trailing characters** — ```` ```" ```` must be ```` ``` ```` (no trailing `"`)
7. **Component tags must have blank lines** — `<Tip>`, `<Warning>`, `<Card>`, `<Accordion>`, `<Note>`, `<Info>` 等组件的标签和内容之间必须有空行
8. **Quote nesting** — if title contains `"`, use `'` for outer attribute; if contains `'`, use `"` for outer attribute

**Mintlify 组件内部必须有空行：**

```mdx
<!-- ❌ 错误：组件标签和内容之间没有空行 -->
<Tip>
这是提示内容。
</Tip>

<!-- ✅ 正确：组件标签和内容之间有空行 -->
<Tip>

这是提示内容。

</Tip>
```

**适用于所有 Mintlify 组件：** `<Accordion>`, `<Steps>`, `<Step>`, `<Tip>`, `<Warning>`, `<Card>`, `<Note>`, `<Info>`

**JSX 属性中的引号嵌套：**

```mdx
<!-- ❌ 错误：属性值中包含双引号 -->
<Accordion title="什么是 "闭包"？">

<!-- ✅ 正确：使用单引号包裹属性 -->
<Accordion title='什么是 "闭包"？'>
<!-- 或者交换引号 -->
<Accordion title="什么是 '闭包'？">
```

**组件内部不要缩进 4 个空格：**

```mdx
<!-- ❌ 错误：缩进 4 个空格会被解析为代码块 -->
<Accordion title="Deep Dive">

    这是第一段。
</Accordion>

<!-- ✅ 正确：不要缩进 -->
<Accordion title="Deep Dive">

这是第一段。

</Accordion>
```

### Banned words

Don't use these in the body text:

- **Attribution verbs as sentence starters**: `根据`, `指出`, `认为`, `表示`, `解释了`
- **AI summary phrases**: `核心观点`, `深度解析`, `xx视角`, `总结来说`, `总而言之`
- **Hype language**: `降维打击`, `黑魔法`, `物理防御`, `一竿子插到底`
- **Source insight**: Use "源码解析" not "源码洞察"

### Template structure

Match `_template.mdx` exactly. The template has **two Q1 modes** — choose based on topic type:

**新增模块清单：**

| 模块 | 文件 | 内容 |
|------|------|------|
| 监控/性能 | `performance/monitoring.mdx` | rrweb、MutationObserver、监控系统搭建 |
| Monorepo | `monorepo/monorepo.mdx` | pnpm、Turborepo、幽灵依赖 |
| Docker | `docker/docker.mdx` | 镜像、容器、Dockerfile、多阶段构建 |
| 微前端 | `micro-frontend/micro-frontend.mdx` | qiankun、wujie、MicroApp、Garfish |
| React Native | `react-native/react-native.mdx` | 版本历史、启动线程、冷热加载、新架构 |
| Taro | `taro/taro.mdx` | 编译时 vs 运行时、双线程模型 |
| uni-app | `uni-app/uni-app.mdx` | 条件编译、跨端原理 |
| RAG | `ai/rag.mdx` | 检索增强生成、向量数据库、企业级 RAG |
| Agent | `ai/agent.mdx` | 企业级 Agent、长时间运行、Harness Engineering |
| Cloudflare Workers | `engineering/cloudflare-workers.mdx` | V8 Isolates、边缘计算、KV/D1/R2 |
| 内存泄漏 | `javascript/memory-leak.mdx` | 常见泄漏场景、Chrome DevTools 排查 |
| 错误处理 | `javascript/error-handling.mdx` | Error 对象、try/catch、Promise 错误 |
| Proxy/Reflect | `javascript/proxy-reflect.mdx` | 13 种 trap、Reflect API、Vue 3 响应式 |
| Service Worker | `javascript/service-worker.mdx` | 生命周期、Cache API、PWA |

- **Mode A (普通话题)**: Q1 has detailed Steps (3-5 sentences each, 5+ steps). For concepts, comparisons, design patterns.
- **Mode B (流程/流程类)**: Q1 has brief Steps (1-2 sentences each). Detailed explanations go in Q2-Q8, one per step. For browser rendering, event loop, HTTP lifecycle, etc.

- Opening: `> **面试官为什么问这个？**` blockquote
- Questions: `## Q1:`, `## Q2:`, etc.
- Q1 must have: `<Steps>` (5+ steps, each 2-3 sentences) + **XXX 解决的核心问题：** code block + `<Note title="💡 一句话总结">` + `<CardGroup>` + `<Tip title="💡 面试技巧">`
- Q2 must have: ASCII diagram + `<Warning>` + `<Tip title="🎢 通俗比喻：XXX">` + 2-3 `###` sub-sections
- Q3: comparison table + `### 专家视角深度剖析` + `###` sub-sections
- Q4: classic pitfall scenarios + `<Tip title="最佳实践：">` + `###` sub-sections
- Source code: `<div class="follow-up">` with GitHub links (specific functions, not directories)
- 满分回答: `## 十、面试官视角：满分回答 vs 及格回答` with 3-4 separate `>` blocks
- 追问链: `### 大厂高频连环拷问` + `<AccordionGroup>` + **8 个 `<Accordion>` items**（4 个难度层级，每个 2 个）
- Bottom: `## 📚 延伸阅读与引用参考` with `<sup>` citations
- **必须使用 `## 📚 延伸阅读与引用参考`**（带 📚 emoji），❌ 严禁使用 `## 延伸阅读与引用参考`（不带 emoji）

### Analogies: knowledge + fun scenario

The `<Tip title="🎢 通俗比喻：...">` must have **two parts**:

1. **知识**（1-2 句）：先用简洁的技术语言解释核心机制
2. **趣味比喻**（2-3 句）：再用生活场景让概念更易记

### CardGroup: knowledge + fun scenario

Each `<Card>` must have **知识+趣味比喻** — start with a technical statement (1-2 sentences), then use a life scenario to illustrate (1-2 sentences).

### Steps: two modes based on topic type

**Mode A: Non-pipeline topics** (concepts, comparisons, design patterns)

The `<Steps>` in Q1 must have **at least 5 steps**. Each step has **2-3 sentences** of detailed explanation.

**Mode B: Pipeline/process topics** (browser rendering, event loop, HTTP lifecycle, etc.)

Q1 is a **medium-length overview** — not detailed. Each Step is a brief introduction (1-2 sentences). The detailed explanations go in Q2-Q8, one Q per step.

**Q1 structure (Mode B):**
1. Flow diagram showing the entire pipeline before Steps
2. Each Step: brief introduction (1-2 sentences), no deep dive
3. After Steps: 解决的核心问题 + 一句话总结 + CardGroup + 面试技巧

**Steps 内容可以是：**
- 技术发展的历史阶段
- 流程的各个阶段
- 流程的关键节点

**Q2-Q8 structure (one Q per pipeline step):**
1. Main content: detailed explanation (3-5 sentences) + ASCII diagram + fun analogy
2. **Sub-sections (`###`)**: extended knowledge topics that go deeper into the Q's subject
3. These sub-sections are NOT interview questions — they are deeper explanations of the topic
4. **每个 Q 下面必须有 2-3 个 `###` 子标题**，用于深入解释该 Q 的主题

**Example sub-sections for a Q section:**
```
## Q4: [主题名称]
[main content with diagram + analogy]

### [扩展知识点 1]
[deeper explanation]

### [扩展知识点 2]
[comparison table + details]

### [扩展知识点 3]
[practical examples]
```

**Important distinction:**
- `###` sub-sections = extended knowledge (deeper explanation of the topic)
- `<Accordion>` items = interview questions (in the 大厂高频连环拷问 section)
- These are different things and should not be confused

### 满分回答: medium-long, 3-4 separate blocks

Each paragraph must be a separate `>` block with a blank line between them. **3-4 paragraphs, each 3-5 sentences**. This is in a collapsible panel, so length is fine — more detail is better.

**Paragraph structure:**
1. **核心问题/设计初衷**（3-5 句）：为什么要有这个技术？解决了什么痛点？
2. **具体机制**（3-5 句）：怎么工作的？**必须有源码函数名、文件路径、或具体数字**，不能只是概念复述
3. **实际踩坑**（3-5 句）：真实项目中会遇到什么问题？**必须有具体的错误场景**
4. **项目建议**（可选，2-3 句）：实际项目中怎么做？

**每个段落必须有至少一个具体数字或源码函数名** — "Promise.then" 不够，要 "V8 的 `MicrotaskQueue::RunMicrotasks()` 用环形缓冲区实现"；"性能差" 不够，要 "每一帧最多给 JS 5ms，剩下 11ms 给浏览器渲染"。

**Format:**
```
> 第 1 段：核心问题...<sup>[1]</sup>

> 第 2 段：具体机制（带源码引用）...<sup>[2]</sup>

> 第 3 段：实际踩坑（带具体场景）...<sup>[3]</sup>

> 第 4 段：项目建议（可选）...
```

### 高分回答: substantial with code examples

Each 高分回答 inside `<Accordion>` must be **5-8 sentences** with code examples where applicable. Must include specific mechanism names or source code references. Cannot be just "concept restatement". Every 高分回答 should have at least one code block.

**高分回答结构（按难度层级）：**
- Level 1-2（基础/机制）：先解释原理，再给代码示例
- Level 3（场景）：先说结论，再分场景讨论，每种场景给代码
- Level 4（杀手题）：先说"不一定"/"分情况"，再对比分析，最后给判断

### Controversial questions: show both sides, then judge

Some interview questions are traps — there's no single correct answer. Answer structure:
1. **表面上的答案**（1 句）
2. **反面的证据**（2-3 句，带具体数据/场景）
3. **你的判断**（2 句）
4. **升华**（1 句）

**争议性问题的扩展模式（举一反三）：**

当遇到有争议的问题时，用以下框架展开：

```
## Q: [争议性问题]

**表面上的答案：**
[大众的普遍认知]

**反面的证据：**
[数据/场景/源码证明相反观点]

**你的判断：**
[分场景讨论，给出明确结论]

**升华：**
[从这个问题延伸到更深层的设计思想]
```

**经典争议性问题示例：**
- 某技术 A 真的比技术 B 快吗？
- 某工具真的能减少 bug 吗？
- 某框架是过度设计吗？
- 某方案真的比替代方案好吗？

**每个争议性问题必须包含：**
1. ❌/✅ 代码对比（展示两种观点的实现）
2. 性能对比数据（如果有）
3. 适用场景分析（什么时候用 A，什么时候用 B）
4. 延伸阅读（权威文章链接）

### Accordion titles

Use the question itself as the title, no "第一层/第二层" prefixes. Keep `🔥` for the hardest question.

### Diagrams: ASCII box-drawing required

Use ASCII art diagrams (┌ ─ ┐ │ └ ┘ ▼ →) to enhance understanding. Q2 must have a flow diagram. Other sections add diagrams when they help (execution order, state transitions, data structures).

### Code comparison: ❌/✅ pattern for pitfalls

When showing common mistakes, use the ❌/✅ code comparison pattern — it's more effective than pure text explanation:

```javascript
// ❌ 错误做法：[一句话说明为什么错]
[错误代码示例]

// ✅ 正确做法：[一句话说明为什么对]
[正确代码示例]
```

This pattern is especially powerful in Q4 (经典踩坑题) and in Warning blocks. Use it whenever showing "what not to do" vs "what to do".

### Source code links

Must link to specific function/method with line number, NOT just directory path:
- ❌ `详见 [Blink 源码 third_party/blink/renderer/core/frame/]`
- ✅ `详见 [Blink 源码 frame_lifecycle.cc](https://chromium.googlesource.com/...)`

### Follow-up questions: real sources, progressive difficulty

The `<AccordionGroup>` follow-up questions must:
1. Be sourced from real interview experiences (牛客网, 掘金, GitHub 面经 repos like haizlin/fe-interview)
2. Be ordered by progressive difficulty: basic → mechanism → scenario → hand-write/killer
3. Each question should have: **答题要点：** + **高分回答：** with code examples
4. **每个模块 8 个 Accordion**，覆盖 4 个难度层级，每个层级 2 个

**Accordion difficulty levels (4 levels, 2 each = 8 total):**

| Level | Icon | Title pattern | Description |
|-------|------|--------------|-------------|
| 1. 基础追问 | `icon="layer-group"` | 从满分回答自然延伸的基础问题 | 测试候选人是否理解基本概念 |
| 2. 机制追问 | `icon="stopwatch"` | 深入规范或底层原理的问题 | 测试候选人是否理解设计初衷 |
| 3. 场景追问 | `icon="node"` | 跨端或边界场景的问题 | 测试候选人是否能分场景讨论 |
| 4. 杀手题 | `icon="skull"` | 极端场景、反直觉的问题（标题加 🔥） | 测试候选人的知识边界 |

### Frontend developer perspective

Explain concepts from the "why should a frontend developer care" angle, not pure academic description. Structure explanations as:
1. **What is it?** — concise technical definition
2. **Why does it matter to me?** — concrete impact on user experience or code
3. **When do I encounter it?** — real scenarios in daily work
4. **What should I do?** — actionable best practices

**Example pattern:**
- What is it? → "[技术定义]"
- Why does it matter? → "[对用户体验或代码的影响]"
- When do I encounter it? → "[实际使用场景]"
- What should I do? → "[可执行的最佳实践]"

### Explanation order: problem first, solution second

When explaining a concept, **always start from the problem/pain point, then introduce the solution**. Don't jump straight to the technology name.

**Pattern (apply to ALL explanations):**
1. **问题**（1-2 句）：这个技术解决什么问题？不解决会怎样？
2. **原理**（2-3 句）：为什么能解决？内部机制是什么？
3. **方案**（2-3 句）：具体怎么用？有哪些 API/工具？
4. **代码**（示例）：实际代码演示

**This forces the writer to:**
- Explain "why" before "what"
- Show the problem before the solution
- Make the reader understand the motivation first
- Never start with "XXX 是 YYY" without context

### LLM Wiki 流程（严格执行）

本项目遵循 Andrej Karpathy 的 LLM Wiki 模式——知识库是**持久化、可积累的活文档**，不是一次性生成的内容。

**三层架构：**

| 层级 | 文件 | 说明 |
|------|------|------|
| **Raw Sources（原始资料）** | `terminologies.md`、`frontend_ai_experts.md`、`tech_company_blogs.md` | 不可修改，只读 |
| **The Wiki（知识库）** | 所有 `.mdx` 文件 | LLM 持续维护、更新、交叉引用 |
| **The Schema（配置）** | `SKILL.md` | 告诉 LLM 怎么维护 wiki |

**严格流程（每次写入必须遵循）：**

```
1. Ingest（摄入）：
   - 读取 3 个知识库文件
   - 联网查询相关专家/博客的实际文章
   - 基于实际文章写内容
   - 正文用 [1]、[2] 引用
   - 延伸阅读列出实际文章链接

2. Query（查询）：
   - 写完的内容可以作为后续模块的参考
   - 交叉引用其他模块的内容

3. Lint（检查）：
   - 检查一致性
   - 修复矛盾
   - 补充缺失
```

**知识库扩展规则：**
- 如果联网查询到的知识是**新专家、新博客、新技术**，追加到现有三个文档
- 扩展前先检查是否已存在，避免重复
- 遵循现有文档的格式和分类

**禁止行为：**
- ❌ 从训练数据直接写内容，不联网查询
- ❌ 凭空捏造专家或博客引用
- ❌ 只"借用"名单里的名字，不实际查询文章
- ❌ 正文不加 `[1]`、`[2]` 引用标号

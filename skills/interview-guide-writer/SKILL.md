---
name: interview-guide-writer
description: Writes and edits MDX files for the frontend interview guide. Use when creating, rewriting, or restructuring any .mdx chapter, or when aligning content to the template format.
---

# Interview Guide Writer

## Quick Start

Read the template at `_template.mdx`, then write your MDX following its exact structure. Before outputting, check your text against the banned words list below.

## Workflows

### Agent 完整工作流（每次执行必须遵循）

**启动 Agent 时，必须在 prompt 中包含以下完整流程：**

```
第一步：读取知识库和规则（必须）
- MINTLIFY_MDX_RULES.md — MDX 语法规则（写 MDX 前必须先读）
- skills/interview-guide-writer/resources/terminologies.md — 术语词典
- skills/interview-guide-writer/resources/frontend_ai_experts.md — 专家名录
- skills/interview-guide-writer/resources/tech_company_blogs.md — 大厂博客库

第二步：穷尽知识库（必须）
- 根据当前主题，找出所有相关的专家和博客
- 国内国外都要查，不能只引用国外来源
- 联网搜索这些专家/博客的实际文章
- 读取文章的实际内容

第三步：基于文章内容写正文（必须）
- 正文内容必须基于实际文章，不是从训练数据写
- 引用格式：正文用 [1]，延伸阅读列出文章链接
- 禁止"装饰性引用"

第四步：知识库不够才联网补充
- 如果知识库中的专家/博客没有相关内容，才用联网大模型补充

第五步：Q 章节不够就延伸或新增
- 如果知识库查到的内容在现有 Q 章节中没有覆盖，延伸 Q 章节
- 如果知识库查到的内容是全新知识点，新增 Q 章节

第六步：联网查到的新专家/博客 → 追加到知识库文件（必须执行）
- terminologies.md：新术语
- frontend_ai_experts.md：新专家
- tech_company_blogs.md：新博客/团队

**⚠️ 所有新增的知识模块必须有迹可循：**
- 每个新增模块必须引用知识库中的专家/博客
- 联网查到的新专家/博客必须追加到知识库文件
- 禁止凭空编造引用来源
- 每个模块的延伸阅读必须有至少 2 个真实来源

第七步：每次写入后记录到 log.txt

第八步：验证流程
- Mintlify 解析错误检查
- 代码块关闭检查
- 国内专家引用检查
- 延伸阅读来源验证
```

### Writing a new chapter

1. Follow the Agent 完整工作流 above
2. Read `_template.mdx` as the structural reference
3. Read `javascript/event-loop.mdx` as the golden reference
4. Research the topic: use web search for source code links, verify URLs aren't 404
5. Search for real interview questions (牛客网, 掘金, GitHub 面经 repos)
6. Write using the template structure (see Rules below)
7. Self-check: no banned words, correct citation format, all links work

### Rewriting an existing chapter

1. Follow the Agent 完整工作流 above
2. Read the existing file
3. Read the template for structural reference
4. Restructure to match template (add missing sections, fix component usage)
5. Preserve technical content, remove AI patterns
6. Add missing diagrams and analogies

## Rules

### Knowledge base: mandatory loading, research, and citation

**STRICT RULE: 知识库是主要来源，不是装饰。每次写入必须遵循以下流程：**

**第一步：读取知识库（必须）**
- `skills/interview-guide-writer/resources/terminologies.md` — 术语词典
- `skills/interview-guide-writer/resources/frontend_ai_experts.md` — 专家名录
- `skills/interview-guide-writer/resources/tech_company_blogs.md` — 大厂博客库

**第二步：穷尽知识库（必须）**
- 根据当前主题，从知识库中找出**所有相关的专家和博客**
- 国内国外都要查，不能只引用国外来源
- 联网搜索这些专家/博客的**实际文章**
- **读取文章的实际内容**，不是只记下文章标题

**第三步：基于文章内容写正文（必须）**
- **正文内容必须基于实际文章**，不是从训练数据写
- 引用格式：正文用 `[1]`，延伸阅读列出文章链接
- **禁止"装饰性引用"**——不能自己写内容，然后找专家名字装饰

**第四步：知识库不够才联网补充**
- 如果知识库中的专家/博客没有相关内容，才用联网大模型补充
- 联网查到的新专家/博客，**追加到知识库文件**

**第四步：Q 章节不够就延伸或新增**
- 如果知识库查到的内容在现有 Q 章节中没有覆盖，**延伸 Q 章节**
- 如果知识库查到的内容是**全新知识点**，**新增 Q 章节**

**引用格式规则：**
- 正文中用 `[1]`、`[2]` 等上标引用，**不提具体专家姓名或博客名称**
- 底部延伸阅读列出具体来源（专家姓名 + 博客链接）
- 每个模块至少引用 3 个来源（国内国外各至少 1 个）

**引用格式示例：**

```markdown
正文：
> [技术原理描述]。<sup>[1]</sup>

延伸阅读：
- 🔗 [专家姓名: 文章标题](链接)：[一句话说明文章价值]。<sup>[1]</sup>
- 📖 [专家姓名: 文章标题](链接)：[一句话说明文章价值]。<sup>[2]</sup>
```

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

**写 MDX 文件前必须先读取 `MINTLIFY_MDX_RULES.md`。**

To avoid "🚧 A parsing error occurred" on Mintlify, follow the rules in `MINTLIFY_MDX_RULES.md`. Key rules:

1. **Never use bare `<` or `>` in text** — always wrap HTML tags in backticks or use HTML entities
2. **Always close JSX tags** — `<Warning>` must have `</Warning>`
3. **Component tags must have blank lines** — `<Tip>`, `<Warning>`, `<Card>`, `<Accordion>`, `<Note>`, `<Info>` 等组件的标签和内容之间必须有空行
4. **Code block closing must NOT have trailing characters** — ```` ```" ```` must be ```` ``` ```` (no trailing `"`)
5. **No code block opening inside another code block**
6. **Quote nesting** — if title contains `"`, use `'` for outer attribute; if contains `'`, use `"` for outer attribute
7. **No 4-space indentation inside components**
8. **No `<script>` tags** — use `[script]` instead
9. **No `<!-- -->` comments** — use `&lt;!-- -->` instead

**禁止行为：**
- ❌ 在已开启的代码块内再开启代码块（会导致解析错误）
- ❌ 在组件标签内使用与外层相同的引号（如 `<Tip title="xxx "yyy"">`）
- ❌ 使用 `sed`、`awk` 等批量工具修复 MDX 文件（会引入新错误）

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

### Analogies: knowledge + fun scenario (每个技术概念必须有)

**每个技术概念必须同时包含图解和趣味比喻，不可省略。**

**图解要求：**
- 使用 ASCII 框线图（┌ ─ ┐ │ └ ┘ ▼ →）
- 展示数据流、执行顺序、架构关系
- 放在技术解释之前或之后

**趣味比喻要求（必须有，不可省略）：**
The `<Tip title="🎢 通俗比喻：...">` must have **two parts**:

1. **知识**（1-2 句）：先用简洁的技术语言解释核心机制
2. **趣味比喻**（2-3 句）：再用生活场景让概念更易记

**比喻来源规则：**
- **原文有比喻** → 直接引用，注明出处
- **原文没有比喻** → 基于原文技术内容生成生活化比喻

**示例（基于 Jake Archibald 的酒店比喻）：**
```
Jake Archibald 用酒店比喻解释 Event Loop：
主线程像酒店经理，一次只能做一件事。
宏任务像排期服务（叫醒、客房服务），按时间表执行。
微任务像紧急投诉，必须立即处理，处理完才能做下一个排期服务。
```

**示例（基于技术内容生成的比喻）：**
```
BFC 就像给房间装隔音门——
没有隔音门时，隔壁噪音传进来（margin 重叠）。
装了隔音门后，噪音传不出去（margin 被隔离）。
```

**适用于所有技术概念：** 0-RTT、Fiber 架构、Proxy 响应式、BFC、Flex 布局等

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

**每个段落必须有至少一个具体数字或源码函数名** — 不能只写 API 名称，要写底层实现细节；不能只写"性能差"，要写具体数字。

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

### 代码输出题：图解 + 代码注释 + 趣味比喻 + 细节

**遇到以下场景时，必须使用「图解 + 代码注释 + 趣味比喻 + 细节」规范：**

1. **代码输出题** - 给一段代码，问输出是什么
2. **原理题** - 解释某个技术的底层原理
3. **需要图解的知识点** - 需要用图来解释的概念

**四步规范：**

**第一步：图解（必须有）**
- 使用 ASCII 框线图展示执行流程
- 展示调用栈、内存结构、状态变化
- 放在代码之前或之后

**第二步：代码注释（必须有）**
- 在代码中添加逐行注释
- 注释要解释"为什么"，不只是"是什么"
- 标注关键的执行时机和状态变化

**第三步：趣味比喻（必须有）**
- 用生活化的场景来解释技术概念
- 比喻要贴切，不能生搬硬套
- 放在 `<Tip title="🎢 通俗比喻：...">` 中

**第四步：细节（必须有）**
- 深入的技术细节和实现原理
- 源码函数名、文件路径、或具体数字
- 不能只是概念复述

**通用规则（适用于任何技术栈）：**

| 步骤 | 目的 | 格式要求 |
|------|------|----------|
| 图解 | 展示执行流程、状态变化、数据流向 | ASCII 框线图，放在代码前或后 |
| 代码注释 | 解释"为什么"，不只是"是什么" | 逐行注释，标注关键时机和状态 |
| 趣味比喻 | 让概念更易记 | 生活化场景，放在 `<Tip>` 中 |
| 细节 | 深入实现原理 | 源码函数名、文件路径、具体数字 |

**示例格式：**

```javascript
// ❌ 错误做法：只给代码和输出
[代码]
// 输出：xxx

// ✅ 正确做法：图解 + 代码注释 + 趣味比喻 + 细节

// 图解：
// ┌─────────────────────────────────────┐
// │ [展示执行流程、状态变化、数据流向]   │
// └─────────────────────────────────────┘

// 代码注释：
[代码]  // [解释为什么，不只是是什么]

// 趣味比喻：
// <Tip title="🎢 通俗比喻：[场景]">
// [生活化场景，让概念更易记]
// </Tip>

// 细节：
// [源码函数名、文件路径、具体数字]
```

**适用场景：** 任何需要解释执行流程、状态变化、数据流向的代码题，不限技术栈。

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

**面试题必须来自真实题库，禁止凭空编造。**

**题库来源（必须联网查询）：**
- 牛客网面经
- 掘金面经
- GitHub 面经 repos（如 haizlin/fe-interview）
- 字节跳动、腾讯、阿里、美团等大厂真实面试题

**联网查询流程：**
1. 搜索"[技术名] 面试题 牛客网"
2. 搜索"[技术名] 面试题 掘金"
3. 搜索"[技术名] 面试题 字节跳动"
4. 提取真实题目
5. 基于真实题目写答案

**禁止行为：**
- ❌ 从训练数据编造面试题
- ❌ 使用"据业内专家所言"等泛泛引用
- ❌ 不联网查询直接写题目

The `<AccordionGroup>` follow-up questions must:
1. **Be sourced from real interview experiences** (牛客网, 掘金, GitHub 面经 repos like haizlin/fe-interview)
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

本项目借鉴 Andrej Karpathy 的 RAG 架构（[karpathy/rag-from-scratch](https://github.com/karpathy/rag-from-scratch)），知识库是**持久化、可积累的活文档**，不是一次性生成的内容。

**三层架构：**

| 层级 | 文件 | 说明 |
|------|------|------|
| **Raw Sources（原始资料）** | `terminologies.md`、`frontend_ai_experts.md`、`tech_company_blogs.md` | 不可修改，只读 |
| **The Wiki（知识库）** | 所有 `.mdx` 文件 | LLM 持续维护、更新、交叉引用 |
| **The Schema（配置）** | `SKILL.md` | 告诉 LLM 怎么维护 wiki |
| **The Log（操作日志）** | `resources/log.txt` | 记录所有摄入、查询、检查操作 |

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
- ❣ 正文不加 `[1]`、`[2]` 引用标号
- ❌ 在已开启的代码块内再开启代码块（会导致解析错误）
- ❌ 在组件标签内使用与外层相同的引号（如 `<Tip title="xxx "yyy"">`）

**代码语言选择规则：**
- LangChain/LangGraph/RAG/Agent 实现 → **Python**（这些是 Python 框架）
- 训练/微调/Embedding → **Python**（这些是 Python 生态）
- 前端集成（React/Vue/浏览器 API）→ **JavaScript**
- 不要写"Python + JavaScript 双语代码"，根据场景选择最合适的语言

**日志记录规则：**
- 每次写入/修改模块后，必须在 `resources/log.txt` 中记录
- 格式：`## [YYYY-MM-DD] action_type | description`
- action_type：`ingest`（摄入新内容）、`query`（查询）、`lint`（检查）

**新增模块规则：**
- 创建新文件后，必须同步更新 `docs.json` 导航结构
- 新模块必须放入正确的 Tab 和分组
- 更新后验证 `docs.json` 格式正确（`python3 -c "import json; json.load(open('docs.json'))"`）

### 验证流程（每次写入后必须执行，不可跳过）

**写入完成后，必须执行以下验证：**

1. **Mintlify 解析错误检查（必须）**
   ```bash
   pkill -9 -f "mintlify" 2>/dev/null || true
   sleep 2
   timeout 30 npx mintlify dev 2>&1 | grep -E "error|parsing|failed" | grep -v "favicon"
   ```
   - 如果有错误，必须立即修复后再提交
   - 常见错误：引号嵌套、代码块尾随字符、组件缺空行

2. **代码块关闭检查**
   ```bash
   grep '```"' <file>  # 应无输出
   ```

3. **引号嵌套检查**
   ```bash
   grep 'title="[^"]*"[^"]*"' <file>  # 应无输出
   ```

4. **国内专家引用检查**
   - 检查正文中是否引用了国内专家
   - 检查延伸阅读中是否有国内来源

5. **延伸阅读来源验证**
   - 检查引用的 URL 是否真实存在
   - 检查专家姓名是否来自知识库
   - 检查是否有国内国外各至少 1 个来源

6. **记录到 log.md**
   - 验证完成后，在 `resources/log.txt` 中记录 lint 结果

**常见解析错误及修复方法：**

| 错误类型 | 原因 | 修复方法 |
|---------|------|---------|
| `Expected a closing tag for <Accordion>` | 代码块内有未闭合的标签 | 检查代码块内的标签是否正确闭合 |
| `Unexpected character "` in attribute name | title 属性有嵌套引号 | 用单引号包裹属性 `title='xxx "yyy"'` |
| `Could not parse expression with acorn` | 代码块内有特殊字符 | 转义或用 HTML 实体 |
| `Expected closing tag for <script>` | log.md 中有 script 标签 | 用 `[script]` 替代 |

**注意：** 引号嵌套检查脚本可能误报（如 Accordion 标题中的 `?` 被误认为引号）。实际检查时应排除 Accordion 标题。

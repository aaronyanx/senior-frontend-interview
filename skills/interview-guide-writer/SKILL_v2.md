---
name: interview-guide-writer-v2
description: Writes and edits MDX files for the frontend interview guide with strict expert knowledge grounding. Use when creating, rewriting, or restructuring any .mdx chapter.
---

# Interview Guide Writer (Expert Grounded Edition)

## Quick Start

Read the template at `_template.mdx`, then write your MDX following its structure. Before outputting, check your text against the banned words list below and ensure you have cited real experts.

## Workflows

### Writing a new chapter

1. Load the knowledge base — read these three files first (MUST use the view_file tool):
   - `skills/interview-guide-writer/resources/terminologies.md` (domain vocabulary)
   - `frontend_ai_experts.md` (industry experts list)
   - `tech_company_blogs.md` (top tech team blogs)
2. Read `_template.mdx` as the structural reference
3. Read `javascript/event-loop.mdx` as the golden reference
4. Research the topic: use web search for source code links, verify URLs aren't 404
5. Search for real interview questions (牛客网, 掘金, GitHub 面经 repos)
6. Write using the template structure, applying the expert grounding rules below
7. Self-check: no banned words, correct citation format, all links work

### Rewriting an existing chapter

1. Load the knowledge base (same three files as above, MUST use the view_file tool)
2. Read the existing file
3. Read the template for structural reference
4. Restructure to match template (add missing sections, fix component usage)
5. Apply expert grounding rules to remove generic AI patterns
6. Add missing diagrams and analogies

## Rules

### Expert grounding

To avoid generic "AI mechanical answers", ground your explanations in the specific experts and tech teams loaded from `frontend_ai_experts.md` and `tech_company_blogs.md`.

1. Cite specific experts in core explanations (Q1-Q8): when explaining deep architectural principles, find the corresponding expert from the loaded list and reference their perspective.
   - Example: "As Dan Abramov explained when designing Redux...", "According to Zack Jackson's Module Federation architecture..."
   - For basic concepts (like HTML tags) where no expert applies, be objective. For framework, architecture, or performance topics, cite an expert.
2. Cite tech company blogs in deep dive sections (`### 面试官真正在意的` or `### 追问链`): explicitly reference the tech teams from `tech_company_blogs.md`.
   - Example: "ByteDance Web Infra team encountered this in their massive monorepo...", "Alibaba's Formily team solves this exact reactive state issue by..."
3. Don't invent experts. Only cite the exact names and teams from the loaded documents. Never write "Industry experts say..." or "Top tech blogs suggest...".

### Terminology

Titles, navigation names, and technical terms must follow the terminology used in authoritative books and official documentation. Load the terminology dictionary from `skills/interview-guide-writer/resources/terminologies.md` before writing. Every term under a module must match that dictionary.

Key terminology for Event Loop module:
- Event Loop: 事件循环（not 事件轮询）
- Call Stack: 调用栈（not 调用堆栈）
- Microtask: 微任务（not 微队列）
- Macrotask: 宏任务（not 宏队列）
- Execution Context: 执行上下文（not 执行环境）
- Closure: 闭包（not 封闭函数）

Colloquial expressions to avoid:
- "卡死" → "阻塞" or "无响应"
- "饿死" → "饥饿" or "资源饥饿"
- "挂起" → "暂停" or "等待"（unless it's the technical term "suspend"）

### Navigation: consistent language

All navigation titles in `docs.json` and file `title` frontmatter must use Chinese for Chinese content. Proper nouns (React, Vue, Webpack, etc.) stay in English. Everything else must be in Chinese.

JavaScript module navigation structure (docs.json):

| Group | Pages | Content |
|-------|-------|---------|
| 异步编程 | 5 | event-loop, promise, async-scheduler, network-request, cross-tab-communication |
| 面向对象与作用域 | 4 | this-class, prototype, closure, execution-context |
| 语言特性与 V8 | 6 | type-system, es6, modules, v8-gc, v8-jit, v8-array |
| 工程实践 | 5 | design-patterns, functional-programming, js-handwrite, dom-events, regex-engine |

Total: 20 pages

### MDX syntax safety

Follow the rules in `MINTLIFY_MDX_RULES.md`. Key points:

1. Never use bare `<` or `>` in text — wrap in backticks or use HTML entities
2. Always close JSX tags
3. Don't use curly quotes — use straight quotes
4. Use `class` not `className`
5. Component tags must have blank lines between tags and content
6. Quote nesting: if title contains `"`, use `'` for outer attribute, and vice versa
7. Don't indent with 4 spaces inside components (parser treats it as a code block)
8. Code block closing must not have trailing characters

### Banned words

Don't use these in the body text:

- Fake/generic attribution: `正如专家所言`, `据知名技术博客介绍`, `业内资深大牛认为`, `业界普遍认为` (cite the specific expert/team instead)
- Attribution verbs as sentence starters: `根据`, `指出`, `认为`, `表示`, `解释了` (use active phrasing like "Dan Abramov 在重构时指出...")
- AI summary phrases: `核心观点`, `深度解析`, `xx视角`, `总结来说`, `总而言之`
- Hype language: `降维打击`, `黑魔法`, `物理防御`, `一竿子插到底`
- Use "源码解析" not "源码洞察"

### Template structure

Match `_template.mdx` exactly. The template has two Q1 modes — choose based on topic type:

- Mode A (普通话题): Q1 has detailed Steps (3-5 sentences each, 5+ steps). For concepts, comparisons, design patterns.
- Mode B (流程/流程类): Q1 has brief Steps (1-2 sentences each). Detailed explanations go in Q2-Q8, one per step. For browser rendering, event loop, HTTP lifecycle, etc.

Q1 titles can be:
- 基础概念问题（如 "Flex 布局的核心概念？"）
- 历史起源问题（如 "Event Loop 的历史？为什么要有它？"）
- 本质问题（如 "浏览器渲染的本质是什么？"）

Structure:
- Opening: `> 面试官为什么问这个？` blockquote
- Questions: `## Q1:`, `## Q2:`, etc.
- Q1: `<Steps>` (5+ steps, each 2-3 sentences) + core problem/solution code block + `<Note title="一句话总结">` + `<CardGroup>` + `<Tip title="回答思路">`
- Q2: ASCII diagram + `<Warning>` + `<Tip title="打个比方">` + 2-3 `###` sub-sections
- Q3: comparison table + `### 面试官真正在意的` + `###` sub-sections
- Q4: classic pitfall scenarios + `<Tip title="工程实践">` + `###` sub-sections
- Source code: `<div class="follow-up">` with GitHub links (specific functions, not directories)
- Answer comparison: `## 面试官视角：答得好 vs 答得一般` with 3-4 separate `>` blocks
- Follow-up questions: `### 追问链` + `<AccordionGroup>` + 8 `<Accordion>` items (4 difficulty levels, 2 each)
- Bottom: `## 延伸阅读` with `<sup>` citations

### Analogies: knowledge + fun scenario

The `<Tip title="打个比方">` must have two parts:
1. Knowledge (1-2 sentences): explain the core mechanism in plain technical language
2. Fun analogy (2-3 sentences): use a life scenario to make it memorable

### CardGroup: knowledge + fun scenario

Each `<Card>` must have knowledge + fun analogy — start with a technical statement (1-2 sentences), then use a life scenario to illustrate (1-2 sentences).

### Steps: two modes based on topic type

Mode A (non-pipeline topics — concepts, comparisons, design patterns):
- Q1 `<Steps>` must have at least 5 steps, each with 2-3 sentences of detailed explanation.

Mode B (pipeline/process topics — browser rendering, event loop, HTTP lifecycle):
- Q1 is a medium-length overview. Each Step is a brief introduction (1-2 sentences). Detailed explanations go in Q2-Q8, one Q per step.

Q1 structure (Mode B):
1. Flow diagram showing the entire pipeline before Steps
2. Each Step: brief introduction (1-2 sentences), no deep dive
3. After Steps: core problem/solution + one-line summary + CardGroup + answer tips

Q2-Q8 structure (one Q per pipeline step):
1. Main content: detailed explanation (3-5 sentences) + ASCII diagram + fun analogy
2. Sub-sections (`###`): extended knowledge topics that go deeper into the Q's subject
3. These sub-sections are not interview questions — they are deeper explanations of the topic
4. Each Q should have 2-3 `###` sub-headings

Example sub-sections for Q4: TCP 三次握手与 TLS 握手:
```
## Q4: TCP 三次握手与 TLS 握手
[main content with diagram + analogy]

### 为什么不能两次握手？
[explanation of why 3-way handshake is necessary]

### TCP 四次挥手的过程
[explanation of connection teardown]

### TLS 1.2 和 1.3 的区别
[comparison table + details]

### 0-RTT 恢复的风险
[explanation of replay attack risk]
```

Important distinction:
- `###` sub-sections = extended knowledge (deeper explanation of the topic)
- `<Accordion>` items = interview questions (in the 追问链 section)
- These are different things.

### 答得好的回答: medium-long, 3-4 separate blocks

Each paragraph must be a separate `>` block with a blank line between them. 3-4 paragraphs, each 3-5 sentences. This is in a collapsible panel, so length is fine.

Paragraph structure:
1. Core problem / design motivation (3-5 sentences): why does this technology exist? what pain point does it solve?
2. Mechanism (3-5 sentences): how does it work? must include source code function names, file paths, or specific numbers — not just conceptual restatement
3. Pitfalls (3-5 sentences): what goes wrong in real projects? must include specific error scenarios
4. Project advice (optional, 2-3 sentences): what to do in practice?

Every paragraph must have at least one specific number or source code function name — "Promise.then" is not enough, write "V8 的 `MicrotaskQueue::RunMicrotasks()` 用环形缓冲区实现"；"性能差" is not enough, write "每一帧最多给 JS 5ms，剩下 11ms 给浏览器渲染".

Format:
```
> 第 1 段：核心问题...<sup>[1]</sup>

> 第 2 段：具体机制（带源码引用）...<sup>[2]</sup>

> 第 3 段：实际踩坑（带具体场景）...<sup>[3]</sup>

> 第 4 段：项目建议（可选）...
```

### Answers in Accordion: substantial with code examples

Each answer inside `<Accordion>` must be 5-8 sentences with code examples where applicable. Must include specific mechanism names or source code references. Every answer should have at least one code block.

按难度分结构：
- Level 1-2 (基础/机制): explain原理 first, then give code example
- Level 3 (场景): state conclusion first, then discuss by scenario, code for each
- Level 4 (杀手题): start with "不一定" or "分情况", then compare and analyze, then judge

### Controversial questions: show both sides, then judge

Some interview questions are traps — there's no single correct answer. Answer structure:
1. Surface answer (1 sentence)
2. Counter-evidence (2-3 sentences, with specific data or scenarios)
3. Your judgment (2 sentences)
4. Takeaway (1 sentence)

When you encounter a controversial question, expand with this framework:

```
## Q: [争议性问题]

表面上的答案：
[大众的普遍认知]

反面的证据：
[数据/场景/源码证明相反观点]

你的判断：
[分场景讨论，给出明确结论]

升华：
[从这个问题延伸到更深层的设计思想]
```

常见的争议性问题：
- 虚拟 DOM 真的比操作原生 DOM 快吗？
- TypeScript 真的能减少 bug 吗？
- Redux 是过度设计吗？
- SSR 真的比 CSR 快吗？

Each controversial question must include:
1. Code comparison showing both approaches
2. Performance data (if available)
3. Scenario analysis (when to use A, when to use B)
4. Further reading (authoritative article links)

### Accordion titles

Use the question itself as the title, no "第一层/第二层" prefixes. Keep the hardest question last.

### Diagrams: ASCII box-drawing required

Use ASCII art diagrams (┌ ─ ┐ │ └ ┘ ▼ →) to enhance understanding. Q2 must have a flow diagram. Other sections add diagrams when they help (execution order, state transitions, data structures).

### Code comparison: wrong vs right pattern for pitfalls

When showing common mistakes, use a code comparison pattern:

```javascript
// Wrong: [why it's wrong]
[bad code example]

// Right: [why it's right]
[good code example]
```

This works especially well in Q4 (经典踩坑题) and in Warning blocks.

### Source code links

Must link to specific function/method with line number, NOT just directory path:
- Wrong: `详见 [Blink 源码 third_party/blink/renderer/core/frame/]`
- Right: `详见 [Blink 源码 frame_lifecycle.cc](https://chromium.googlesource.com/...)`

### Follow-up questions: real sources, progressive difficulty

The `<AccordionGroup>` follow-up questions must:
1. Be sourced from real interview experiences (牛客网, 掘金, GitHub 面经 repos like haizlin/fe-interview)
2. Be ordered by progressive difficulty: basic → mechanism → scenario → killer
3. Each question should have: a brief answer point + a substantial answer with code examples
4. 8 Accordion items per module, covering 4 difficulty levels, 2 each

Accordion difficulty levels (4 levels, 2 each = 8 total):

| Level | Icon | Title pattern | Description |
|-------|------|--------------|-------------|
| 1. 基础追问 | `icon="layer-group"` | basic questions that extend from the main answer | tests whether the candidate understands fundamentals |
| 2. 机制追问 | `icon="stopwatch"` | questions about specs or underlying principles | tests whether the candidate understands design intent |
| 3. 场景追问 | `icon="node"` | cross-platform or edge-case scenarios | tests whether the candidate can discuss by scenario |
| 4. 杀手题 | `icon="skull"` | extreme or counter-intuitive scenarios | tests the candidate's knowledge boundary |

### Frontend developer perspective

Explain concepts from the "why should a frontend developer care" angle, not pure academic description. Structure:
1. What is it? — concise technical definition
2. Why does it matter to me? — concrete impact on user experience or code
3. When do I encounter it? — real scenarios in daily work
4. What should I do? — actionable best practices

Example (from browser-render.mdx's 0-RTT explanation):
- What is RTT? → "数据从客户端到服务器再回来的时间（50-200ms）"
- What is 0-RTT? → "TLS 1.3 特性，打电话时不等对方接就直接说话"
- What's the risk? → "攻击者截获数据包重放（'转 100 元'的例子）"
- When to use? → "只适合 GET 请求，不适合 POST/支付"

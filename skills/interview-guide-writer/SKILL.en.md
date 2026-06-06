---
name: interview-guide-writer
description: Writes and edits MDX files for the frontend interview guide. Use when creating, rewriting, or restructuring any .mdx chapter in the guide, or when aligning content to the template format.
---

# Interview Guide Writer

## Quick Start

Read the template at `resources/template_event-loop.mdx`, then write your MDX following its structure. Before outputting, check your text against the banned words list below.

## Workflows

### Writing a new chapter

1. Read `resources/template_event-loop.mdx` as the structural reference
2. Research the topic: use web search for source code links, verify URLs aren't 404
3. Search for real interview questions (牛客网, 掘金, GitHub 面经仓库) — don't fabricate
4. Write using the template structure (see Rules below)
5. Self-check: no banned words, correct citation format, all links work, diagrams present

### Rewriting an existing chapter

1. Read the existing file
2. Read the template for structural reference
3. Restructure to match template (add missing sections, fix component usage)
4. Preserve technical content, remove AI patterns
5. Add missing diagrams and analogies

## Rules

### Terminology: use professional terms from authoritative sources

Titles, navigation names, and technical terms must follow the terminology used in authoritative books and official documentation for that domain. Do not invent terms.

| Domain | Authoritative Sources | Examples |
|--------|----------------------|----------|
| JavaScript | 《JavaScript 高级程序设计》、《JavaScript 权威指南》（犀牛书）、MDN | "执行上下文" not "执行环境"，"闭包" not "封闭函数" |
| CSS | 《CSS 新世界》（张鑫旭）、MDN | "块格式化上下文" not "块级格式化环境"，"层叠上下文" not "堆叠上下文" |
| Vue | Vue 官方文档、《Vue.js 设计与实现》（霍春阳） | "响应式" not "数据绑定"，"组合式 API" not "组合 API" |
| React | React 官方文档、React 源码注释 | "Fiber" not "纤程"，"并发模式" not "异步模式" |
| TypeScript | TypeScript 官方文档、《TypeScript 编程》 | "泛型" not "通用类型"，"类型守卫" not "类型检查" |
| 构建工具 | Webpack/Vite 官方文档 | "Tree Shaking" not "摇树优化"，"HMR" not "热替换" |
| AI 工程 | LangChain/LangGraph/MCP 官方文档 | "Agent" not "智能体"，"Tool" not "工具函数" |
| 浏览器 | Chrome DevTools 文档、V8/Blink 源码注释 | "合成层" not "复合层"，"重排" not "回流" |

When in doubt, check the official documentation or the most widely-used book in that domain.

Every term, title, and concept under a module MUST use the terminology from that domain's authoritative source. Do NOT invent terms.

- Under JavaScript module → use terms from 《JavaScript 高级程序设计》（红宝书）和 《JavaScript 权威指南》（犀牛书）
- Under CSS module → use terms from 《CSS 新世界》（张鑫旭）
- Under Vue module → use terms from Vue 官方文档
- Under React module → use terms from React 官方文档
- Under 浏览器 module → use terms from Chrome DevTools 文档、V8/Blink 源码注释
- Under 工程化 module → use terms from Webpack/Vite/GitHub Actions 官方文档
- Under AI 工程化 module → use terms from LangChain/LangGraph/MCP 官方文档

### Navigation: consistent language

All navigation titles in `docs.json` and file `title` frontmatter must use Chinese for Chinese content. Do NOT mix English and Chinese in navigation titles.

- Wrong: `"title": "React Fiber"` (English)
- Right: `"title": "React Fiber 架构"` (Chinese with English proper noun)
- Wrong: `"title": "Flex 弹性布局"` → `"title": "Flex 布局"` (keep proper nouns in English, rest in Chinese)

Proper nouns (React, Vue, Webpack, Vite, TypeScript, etc.) stay in English. Everything else must be in Chinese.

### MDX syntax safety

To avoid "🚧 A parsing error occurred" on Mintlify:

1. Never use `<` or `>` in plain text — always escape with `&lt;` and `&gt;` or wrap in code blocks
2. Always close JSX tags — `<Warning>` must have `</Warning>`, `<Tip>` must have `</Tip>`
3. Don't use curly quotes — use straight quotes `"..."` not `"..."`
4. Don't use HTML comments `<!-- -->` inside MDX — use `{/* */}` or remove them
5. Code blocks must be properly fenced — ``` must have matching closing ```

### Banned words

Don't use these in the body text:

- Attribution verbs as sentence starters: `根据`, `指出`, `认为`, `表示`, `解释了`
- AI summary phrases: `核心观点`, `深度解析`, `xx视角`, `总结来说`, `总而言之`
- Hype language: `降维打击`, `黑魔法`, `物理防御`, `一竿子插到底`

### Citation format

1. Don't use expert/company names as sentence subjects. Never write "xx 指出...".
2. Correct format: state the technical fact + end with `<sup>[n]</sup>`.
3. Put source links and expert names in `## 延伸阅读` at the bottom.
4. Get technical material from `resources/` directory files.

### Template structure

Match `resources/template_event-loop.mdx` exactly:

- Opening: `> 面试官为什么问这个？` blockquote
- Questions: `## Q1:`, `## Q2:`, etc.
- Q1 must have: `<Steps>` with at least 5 steps, each step with 2-3 sentences of detailed explanation (not just 1 sentence). Then: a core problem/solution code block + one-line summary + `<CardGroup>` + `<Tip title="回答思路">`
- Q2 must have: ASCII diagram + `<Warning>` + `<Tip title="打个比方">`
- `<CardGroup>` format: each `<Card>` must have knowledge + fun analogy — start with a technical statement (1-2 sentences), then use a life scenario to illustrate (1-2 sentences). Title should be `没有 XXX 的时候` / `引入 XXX 之后` or similar natural phrasing.
  - Wrong (tech only, no analogy): `每个响应式属性都有一个独立的 Watcher，直接绑定到具体的 DOM 节点。`
  - Wrong (analogy only, no tech): `就像一家餐厅，又当服务员又当厨师。`
  - Right (tech + analogy): `单线程同步执行——遇到网络请求时主线程必须等待，整个页面卡住。就像一家餐厅，又当服务员又当厨师，客人点完单你跑去炒菜，新来的客人只能干等着。`
- Deep analysis section: `### 面试官真正在意的`
- Source code: `<div class="follow-up">` with GitHub links — must link to specific function/method with line number, NOT just directory path
  - Wrong: `详见 [Blink 源码 third_party/blink/renderer/core/frame/]`
  - Right: `详见 [Blink 源码 third_party/blink/renderer/core/frame/frame_lifecycle.cc](https://chromium.googlesource.com/chromium/src/+/main:third_party/blink/renderer/core/frame/frame_lifecycle.cc)`
  - Use "源码解析" not "源码洞察"
- Follow-up questions: `### 追问链` + `<AccordionGroup>` + `<Accordion icon="...">`
  - Each answer should be substantial (3-5 sentences) with code examples where relevant
  - Explain the "why" behind the answer, not just state facts
- Bottom: `## 延伸阅读`

### Steps: detailed and substantial

The `<Steps>` component in Q1 must have at least 5 steps. Each step must have 2-3 sentences of detailed explanation — not just a title and one line.

Too brief:
```
<Step title="HTTP 协议诞生">
  Tim Berners-Lee 发明了万维网。HTTP/0.9 只有 GET 请求。
</Step>
```

Detailed:
```
<Step title="1991年：HTTP 协议诞生与单线程宿命">
  Tim Berners-Lee 在 CERN 发明了万维网。最初的 HTTP/0.9 极其简单——只有 GET 请求，没有 Header，响应就是纯 HTML 文本。浏览器拿到 HTML 直接渲染，没有 CSS、没有 JS、没有图片优化。这个阶段的"渲染"就是把文本显示在屏幕上，没有任何布局计算。
</Step>
```

### Answers: substantial with code examples

Each answer inside `<Accordion>` should be 3-5 sentences with code examples where applicable. It should explain the "why" behind the answer, not just state facts.

Too brief:
"Proxy 是 ES6 特性，无法 polyfill。"

Substantial:
"Proxy 是 ES6 特性，无法用 polyfill 模拟——因为 Proxy 拦截的是语言层面的对象操作（get、set、delete），这不是简单的 API 可以模拟的。Vue 3 选择 Proxy 的原因有三个：
1. 拦截范围：能拦截所有操作（新增/删除属性、数组下标、has、ownKeys），defineProperty 做不到。
2. 惰性代理：只有访问到的属性才会被递归代理。
3. 性能：Proxy 的 get/set trap 调用开销约 0.01μs。
这是一个架构层面的取舍——用 IE 兼容性换来了更强大的响应式能力。"

### Analogies: knowledge + fun scenario

The `<Tip title="打个比方">` must have two parts:

1. Knowledge (1-2 sentences): explain the core mechanism in plain technical language
2. Fun analogy (2-3 sentences): use a life scenario to make it memorable

Format:
```
<Tip title="打个比方">
[技术机制]的核心是[一句话概括]。
[生活场景描述——用具体、生动、有画面感的例子]。
[回扣技术——把生活场景和技术概念对应起来]。
</Tip>
```

Wrong (analogy only, no tech):
"想象你在重新安排教室座位。Vue 2 的做法是从第一排和最后一排同时开始核对..."

Wrong (tech only, no analogy):
"Proxy 的 get trap 在属性访问时插入拦截器，track 函数把当前 effect 收集到 dep 中。"

Right (knowledge + analogy):
"依赖收集的本质是'谁访问了数据，谁就被记录下来'。就像你去报刊亭说'我要订阅《时尚杂志》'，报刊亭就把你的名字记在订阅列表上。杂志到了按列表寄给你。你不订阅，杂志到了也不会寄给你。"

Good analogy domains: restaurants, classrooms, shopping, traffic, delivery, libraries, hospitals, amusement parks.

### Diagrams: ASCII box-drawing required

Use ASCII art diagrams (┌ ─ ┐ │ └ ┘ ▼ →) to enhance understanding. Use the same style as `resources/template_event-loop.mdx`.

When to add a diagram:
- Always add for Q2: The core mechanism/algorithm section always needs a flow diagram.
- Add when it helps: Execution order/timing (Event Loop stages), state transitions (reactive → destructuring → loses Proxy), data structure relationships (three-layer Map), or comparison flows (virtual DOM vs Vapor).
- Skip when text is enough: Step-by-step code analysis, comparison tables, interview strategy tips, or sections where code examples already illustrate the point clearly.

Required diagrams:
- Q1: The core problem/solution flow
- Q2: The mechanism/algorithm flow
- Q5 (if exists): Batch update or scheduling flow

Optional but recommended diagrams (add if they enhance understanding):
- Q3: Comparison flow (if comparing two mechanisms, not just a table)
- Q4: State transition flow (if showing how something breaks or changes)
- 底层源码: Data structure or algorithm flow (if the code is complex)

### 答得好的回答：3-4 段，每段 3-5 句

The "答得好的" answer should be 3-4 paragraphs, each 3-5 sentences. It's in a collapsible panel, so length is fine.

Paragraph structure:
1. Core problem / design motivation: why does this technology exist? what pain point does it solve?
2. Mechanism: how does it work? must include source code function names, file paths, or specific numbers (not just conceptual restatement)
3. Pitfalls: what goes wrong in real projects? must include specific error scenarios (not just generic advice)
4. Project advice (optional): what to do in practice?

Each paragraph must be a separate `>` block with a blank line between them:

```
> 第 1 段：核心问题...

> 第 2 段：具体机制（带源码引用）...<sup>[1]</sup>

> 第 3 段：实际踩坑（带具体场景）...<sup>[2]</sup>

> 第 4 段：项目建议...<sup>[3]</sup>
```

### Controversial questions: show both sides, then judge

Some interview questions are traps — there's no single correct answer (e.g., "虚拟DOM比原生DOM快吗？", "CSS动画比JS动画好吗？"). Answering "快" or "慢" is both wrong.

Answer structure for controversial questions:

1. Surface answer: what most people think (1 sentence)
2. Counter-evidence: but actually... (2-3 sentences, with specific data or scenarios)
3. Your judgment: when A is right, when B is right (2 sentences)
4. Takeaway: the real value of this question is understanding the trade-off (1 sentence)

Example (虚拟DOM比原生DOM快吗？):
> 表面上：虚拟 DOM 比直接操作 DOM 快。
> 反面：虚拟 DOM 每次更新都要创建新的虚拟树、diff、再应用到真实 DOM。如果你精确地知道哪些 DOM 需要更新，直接操作 DOM 肯定更快——因为虚拟 DOM 多了一步 diff 计算。
> 判断：虚拟 DOM 的价值不在于"快"，而在于"足够快"+"声明式编程"。对于大多数场景，diff 的开销远小于 DOM 操作的开销；对于极端性能场景（如每帧更新大量节点），直接操作 DOM 或用 Vapor/Svelte 更快。
> 升华：虚拟 DOM 是"开发体验"和"运行性能"之间的最优折中，不是性能的极限。

### Follow-up questions: real sources, progressive difficulty

The `<AccordionGroup>` follow-up questions must:
1. Be sourced from real interview experiences (牛客网, 掘金, GitHub 面经 repos like haizlin/fe-interview)
2. Be updated within the last 1-2 years
3. Be ordered by progressive difficulty: basic → mechanism → scenario → hand-write/killer
4. Each question should have: a brief answer point + a substantial answer with specific code examples where relevant
5. If you can't verify a question is real, note it or omit it
6. Title format: use the question itself as the title, no "第一层/第二层" prefixes. Keep the hardest question last.
   - Wrong: `<Accordion title="第一层：Proxy 有什么缺点？">`
   - Right: `<Accordion title="Proxy 有什么缺点？">`

### Link validation

When writing GitHub source links or external URLs:

1. Use web search to confirm the link exists
2. Verify the URL returns 200, not 404
3. If a link is dead, search for the current valid URL

## Examples

### Citing an architect's view

Wrong: 根据 xx 在官方博客中指出，xx 放弃了 xx 而采用了 xx。

Right: xx 放弃了对 xx 的遍历劫持，转而用 xx 实现了对 xx 的代理拦截<sup>[1]</sup>。

### Source code analysis

Wrong: 专家圆桌深度解析源码：在这里给大家深度解析一下底层源码结构。

Right: **源码**：xx 的数据结构定义在 `packages/xx/src/xx.ts#L89`：

```javascript
// code here
```

### Analogy (good vs bad)

Wrong: 通俗比喻：Proxy 的 get trap 就像在属性访问时插入了一个拦截器，track 函数把当前 effect 收集到 dep 中。

Right: 通俗比喻：订阅杂志——你去报刊亭说"我要订阅《时尚杂志》"，报刊亭就把你的名字记在订阅列表上。杂志到了按列表寄给你。你不订阅，杂志到了也不会寄。

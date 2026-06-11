---
name: interview-guide-writer
description: Writes and edits MDX files for the frontend interview guide. Use when creating, rewriting, or restructuring any .mdx chapter, or when aligning content to the template format.
---

# Interview Guide Writer

## Quick Start

Read `_template.mdx` for structure, read `javascript/event-loop.mdx` as the golden reference, then write following the rules below.

## Agent 工作流

每次写入必须按以下流程执行，不可跳过步骤：

```
第一步：读取知识库和规则（必须）
- MINTLIFY_MDX_RULES.md — MDX 语法规则
- skills/interview-guide-writer/resources/terminologies.md — 术语词典
- skills/interview-guide-writer/resources/frontend_ai_experts.md — 专家名录
- skills/interview-guide-writer/resources/tech_company_blogs.md — 大厂博客库

第二步：知识库全量检索（必须）
- 根据当前主题，找出所有相关的专家和博客
- 国内国外都要查，不能只引用国外来源
- 联网搜索这些专家/博客的实际文章
- 读取文章的实际内容，不是只记下标题

第三步：基于文章内容写正文（必须）
- 正文内容必须基于实际文章，不是从训练数据写
- 引用格式：正文用 [1]、[2]，延伸阅读列出文章链接
- 每个模块至少 3 个来源（国内国外各至少 1 个）
- 禁止"装饰性引用"——不能自己写内容然后找专家名字装饰

第四步：知识库不够才联网补充
- 知识库中的专家/博客没有相关内容时，才用联网搜索补充
- 联网查到的新专家/博客，追加到知识库文件

第五步：Q 章节不够就延伸或新增
- 知识库查到的内容在现有 Q 章节中没有覆盖 → 延伸 Q 章节
- 知识库查到的内容是全新知识点 → 新增 Q 章节

第六步：追加新知识到知识库（必须执行）
- terminologies.md：新术语
- frontend_ai_experts.md：新专家
- tech_company_blogs.md：新博客/团队
- 追加前先检查是否已存在，避免重复

第七步：记录到 resources/log.txt
- 格式：## [YYYY-MM-DD] action_type | description
- action_type：ingest（摄入）、query（查询）、lint（检查）

第八步：验证
- Mintlify 解析错误检查
- 引用格式和来源验证
```

**引用格式：**

```markdown
正文：
> [技术原理描述]。<sup>[1]</sup>

延伸阅读：
- 🔗 [专家姓名: 文章标题](链接)：[一句话说明文章价值]。<sup>[1]</sup>
- 📖 [专家姓名: 文章标题](链接)：[一句话说明文章价值]。<sup>[2]</sup>
```

正文用 `[1]`、`[2]` 上标引用，不提具体专家姓名或博客名称。底部延伸阅读列出具体来源。

### Writing a new chapter

1. Follow the Agent 工作流 above
2. Read `_template.mdx` as structural reference
3. Read `javascript/event-loop.mdx` as golden reference
4. Research the topic: verify URLs aren't 404
5. Search for real interview questions (牛客网, 掘金, GitHub 面经 repos)
6. Write using template structure
7. Self-check: no banned words, correct citations, all links work

### Rewriting an existing chapter

1. Follow the Agent 工作流 above
2. Read the existing file
3. Restructure to match template (add missing sections, fix component usage)
4. Preserve technical content, remove AI patterns
5. Add missing diagrams and analogies

## Rules

### Navigation: consistent language

All navigation titles in `docs.json` and file `title` frontmatter must use **Chinese**. Proper nouns (React, Vue, Webpack, etc.) stay in English.

**JavaScript 模块导航结构（docs.json）：**

| 分组 | 页面数 | 内容 |
|------|--------|------|
| 异步编程 | 5 | event-loop, promise, async-scheduler, network-request, cross-tab-communication |
| 面向对象与作用域 | 4 | this-class, prototype, closure, execution-context |
| 语言特性与 V8 | 6 | type-system, es6, modules, v8-gc, v8-jit, v8-array |
| 工程实践 | 5 | design-patterns, functional-programming, js-handwrite, dom-events, regex-engine |

**总计：20 个页面**

### MDX syntax safety

**写 MDX 文件前必须先读取 `MINTLIFY_MDX_RULES.md`。** Key rules:

1. Never use bare `<` or `>` in text — wrap in backticks or use HTML entities
2. Always close JSX tags — `<Warning>` must have `</Warning>`
3. Component tags must have blank lines between tag and content
4. Code block closing must NOT have trailing characters — ```` ```" ```` → ```` ``` ````
5. No code block opening inside another code block
6. Quote nesting — if title contains `"`, use `'` for outer attribute
7. No 4-space indentation inside components
8. No `<script>` tags — use `[script]` instead
9. No `<!-- -->` comments — use `&lt;!-- -->` instead

**禁止行为：**
- ❌ 在已开启的代码块内再开启代码块
- ❌ 在组件标签内使用与外层相同的引号（如 `<Tip title="xxx "yyy"">`）
- ❌ 使用 `sed`、`awk` 等批量工具修复 MDX 文件

### Banned words

Don't use these in the body text:

- **Attribution verbs as sentence starters**: `根据`, `指出`, `认为`, `表示`, `解释了`
- **AI summary phrases**: `核心观点`, `深度解析`, `xx视角`, `总结来说`, `总而言之`
- **Hype language**: `降维打击`, `黑魔法`, `物理防御`, `一竿子插到底`
- **Source insight**: Use "源码解析" not "源码洞察"

### 禁止使用的口语化表达

- ❌ "卡死" → ✅ "阻塞" 或 "无响应"
- ❌ "饿死" → ✅ "饥饿" 或 "资源饥饿"
- ❌ "挂起" → ✅ "暂停" 或 "等待"（除非是技术术语 "suspend"）

### Template structure

Match `_template.mdx` exactly. The template has **two Q1 modes** — choose based on topic type:

- **Mode A (普通话题)**: Q1 has detailed Steps (3-5 sentences each, 5+ steps). For concepts, comparisons, design patterns.
- **Mode B (流程类)**: Q1 has brief Steps (1-2 sentences each). Detailed explanations go in Q2-Q8, one per step. For browser rendering, event loop, HTTP lifecycle, etc.

**页面结构：**

- Opening: `> **面试官为什么问这个？**` blockquote
- Questions: `## Q1:`, `## Q2:`, etc.
- Q1 must have: `<Steps>` (5+ steps) + **XXX 解决的核心问题：** code block + `<Note title="💡 一句话总结">` + `<CardGroup>` + `<Tip title="💡 面试技巧">`（可选）
- Q2 must have: ASCII diagram + `<Warning>` + `<Tip title="🎢 通俗比喻：XXX">` + 2-3 `###` sub-sections
- Q3: comparison table + `### 专家视角深度剖析` + `###` sub-sections
- Q4: classic pitfall scenarios + `<Tip title="最佳实践：">` + `###` sub-sections
- Source code: `<div class="follow-up">` with GitHub links (specific functions, not directories)
- 满分回答: `## 十、面试官视角：满分回答 vs 及格回答`
- 追问链: `### 大厂高频连环拷问` + `<AccordionGroup>` + **8 个 `<Accordion>` items**（4 个难度层级，每个 2 个）
- Bottom: `## 📚 延伸阅读与引用参考`（带 📚 emoji，不可省略）

### Analogies: knowledge + fun scenario

每个技术概念必须同时包含图解和趣味比喻，不可省略。

**图解：** ASCII 框线图（┌ ─ ┐ │ └ ┘ ▼ →），展示数据流、执行顺序、架构关系。

**趣味比喻（`<Tip title="🎢 通俗比喻：...">`）必须有两部分：**

1. **知识**（1-2 句）：简洁的技术语言解释核心机制
2. **趣味比喻**（2-3 句）：生活场景让概念更易记

**比喻来源：** 原文有比喻就引用出处，没有就基于技术内容生成。

**示例（基于专家比喻）：**
```
Jake Archibald 用酒店比喻解释 Event Loop：
主线程像酒店经理，一次只能做一件事。
宏任务像排期服务，按时间表执行。
微任务像紧急投诉，必须立即处理。
```

**示例（自生成比喻）：**
```
BFC 就像给房间装隔音门——
没有隔音门时，隔壁噪音传进来（margin 重叠）。
装了隔音门后，噪音传不出去（margin 被隔离）。
```

### CardGroup

Each `<Card>` must have **知识+趣味比喻** — 技术陈述（1-2 句）+ 生活场景（1-2 句）。

### Steps: two modes

**Mode A (非流程类):** `<Steps>` 至少 5 步，每步 2-3 句详细解释。

**Mode B (流程类):** Q1 是中等长度概述，每步 1-2 句简介。详细解释放在 Q2-Q8，一个 Q 对应一个步骤。

**Q2-Q8 结构（Mode B）：**
1. 主内容：详细解释（3-5 句）+ ASCII 图 + 趣味比喻
2. **`###` 子标题**：扩展知识点，深入解释该 Q 的主题（每个 Q 下 2-3 个）
3. 子标题不是面试题，是更深层的知识解释

### 满分回答: 3-4 separate blocks

Each paragraph is a separate `>` block with blank line between. **3-4 段，每段 3-5 句。**

**段落结构：**
1. **核心问题/设计初衷**（3-5 句）
2. **具体机制**（3-5 句）— 必须有源码函数名、文件路径、或具体数字
3. **实际踩坑**（3-5 句）— 必须有具体的错误场景
4. **项目建议**（可选，2-3 句）

**每个段落必须有至少一个具体数字或源码函数名。**

```
> 第 1 段：核心问题...<sup>[1]</sup>

> 第 2 段：具体机制（带源码引用）...<sup>[2]</sup>

> 第 3 段：实际踩坑（带具体场景）...<sup>[3]</sup>

> 第 4 段：项目建议（可选）...
```

### 高分回答: 5-8 sentences with code

Each 高分回答 inside `<Accordion>` must be **5-8 sentences** with code examples. Must include specific mechanism names or source code references. Every 高分回答 should have at least one code block.

**按难度层级：**
- Level 1-2（基础/机制）：先解释原理，再给代码示例
- Level 3（场景）：先说结论，再分场景讨论，每种场景给代码
- Level 4（杀手题）：先说"不一定"/"分情况"，再对比分析，最后给判断

### Controversial questions: show both sides, then judge

1. **表面上的答案**（1 句）
2. **反面的证据**（2-3 句，带具体数据/场景）
3. **你的判断**（2 句）
4. **升华**（1 句）

**每个争议性问题必须包含：**
1. ❌/✅ 代码对比
2. 性能对比数据（如果有）
3. 适用场景分析
4. 延伸阅读

### Accordion titles

Use the question itself as the title, no "第一层/第二层" prefixes. Keep `🔥` for the hardest question.

**Accordion difficulty levels (4 levels, 2 each = 8 total):**

| Level | Icon | Description |
|-------|------|-------------|
| 1. 基础追问 | `icon="layer-group"` | 从满分回答自然延伸的基础问题 |
| 2. 机制追问 | `icon="stopwatch"` | 深入规范或底层原理的问题 |
| 3. 场景追问 | `icon="node"` | 跨端或边界场景的问题 |
| 4. 杀手题 | `icon="skull"` | 极端场景、反直觉的问题（标题加 🔥） |

### Diagrams: ASCII box-drawing required

Use ASCII art (┌ ─ ┐ │ └ ┘ ▼ →) to enhance understanding. Q2 must have a flow diagram. Other sections add diagrams when they help.

### 代码输出题：图解 + 代码注释 + 趣味比喻 + 细节

遇到代码输出题、原理题、需要图解的知识点时，用四步规范：

| 步骤 | 目的 | 格式 |
|------|------|------|
| 图解 | 展示执行流程、状态变化 | ASCII 框线图，放在代码前或后 |
| 代码注释 | 解释"为什么" | 逐行注释，标注关键时机 |
| 趣味比喻 | 让概念更易记 | 生活化场景，放在 `<Tip>` 中 |
| 细节 | 深入实现原理 | 源码函数名、文件路径、具体数字 |

### Code comparison: ❌/✅ pattern

When showing common mistakes, use ❌/✅ code comparison:

```javascript
// ❌ 错误做法：[一句话说明为什么错]
[错误代码]

// ✅ 正确做法：[一句话说明为什么对]
[正确代码]
```

Especially powerful in Q4 (经典踩坑题) and Warning blocks.

### Source code links

Must link to specific function/method with line number, NOT directory path:
- ❌ `详见 [Blink 源码 third_party/blink/renderer/core/frame/]`
- ✅ `详见 [Blink 源码 frame_lifecycle.cc](https://chromium.googlesource.com/...)`

### Follow-up questions: real sources, progressive difficulty

**面试题必须来自真实题库，禁止凭空编造。**

**题库来源（必须联网查询）：** 牛客网面经、掘金面经、GitHub 面经 repos（如 haizlin/fe-interview）、字节/腾讯/阿里/美团真实面试题。

**禁止行为：**
- ❌ 从训练数据编造面试题
- ❌ 使用"据业内专家所言"等泛泛引用
- ❌ 不联网查询直接写题目

The `<AccordionGroup>` follow-up questions must:
1. Be sourced from real interview experiences
2. Be ordered by progressive difficulty: basic → mechanism → scenario → killer
3. Each question should have: **答题要点：** + **高分回答：** with code examples
4. 每个模块 8 个 Accordion，4 个难度层级，每个 2 个

### Frontend developer perspective

Explain from "why should a frontend developer care" angle:
1. **What is it?** — concise technical definition
2. **Why does it matter to me?** — impact on user experience or code
3. **When do I encounter it?** — real scenarios in daily work
4. **What should I do?** — actionable best practices

### Explanation order: problem first, solution second

Always start from the problem/pain point, then introduce the solution:
1. **问题**（1-2 句）：解决什么问题？不解决会怎样？
2. **原理**（2-3 句）：为什么能解决？内部机制是什么？
3. **方案**（2-3 句）：具体怎么用？有哪些 API/工具？
4. **代码**（示例）：实际代码演示

Never start with "XXX 是 YYY" without context.

### 代码语言选择

用跟话题最相关的语言，不要为了"全面"写多语言版本：
- 框架/工具的代码示例 → 用该框架的官方语言
- 底层原理 → 用源码实现的语言
- 集成/调用 → 用目标平台的语言
- 不确定时 → 选读者最可能用的那个，只写一种

### 新增模块规则

- 创建新文件后，必须同步更新 `docs.json` 导航结构
- 新模块必须放入正确的 Tab 和分组
- 更新后验证 `docs.json` 格式正确（`python3 -c "import json; json.load(open('docs.json'))"`）

### 验证流程（每次写入后执行）

1. **Mintlify 解析错误检查**
   ```bash
   pkill -9 -f "mintlify" 2>/dev/null || true
   sleep 2
   timeout 30 npx mintlify dev 2>&1 | grep -E "error|parsing|failed" | grep -v "favicon"
   ```

2. **AI 痕迹检查** — 用 `/humanizer` 工具扫描正文，去除 AI 写作模式（过度强调意义、三段式、破折号滥用、套话等）。如果环境没有 `/humanizer`，手动检查：去掉"作为 XX 的重要里程碑"、"不仅...更是..."、滥用破折号、emoji 装饰标题等 AI 腔

3. **代码块关闭检查** — `grep '```"' <file>` 应无输出

4. **引号嵌套检查** — `grep 'title="[^"]*"[^"]*"' <file>` 应无输出（排除 Accordion 标题中的 `?` 误报）

5. **来源验证** — 检查 URL 是否真实存在，专家姓名是否来自知识库，国内国外各至少 1 个来源

6. **记录到 resources/log.txt**

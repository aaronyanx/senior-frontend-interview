# Mintlify MDX Syntax & Development Guidelines

Mintlify uses MDX 2, which treats Markdown as a React JSX component tree. That means certain things that work fine in regular Markdown will break here. This file covers the rules that prevent `A parsing error occurred` crashes.

## 1. Blank lines inside components

When wrapping Markdown text inside Mintlify custom components (`<Accordion>`, `<Steps>`, `<Step>`, `<Tip>`, `<Warning>`, `<Card>`, `<Note>`, `<Info>`), leave at least one blank line between the component's opening/closing tags and the inner Markdown content.

Wrong (parser swallows the inner Markdown):
```mdx
<Tip>
This is the tip content.
</Tip>
```

Right:
```mdx
<Tip>

This is the tip content.

</Tip>
```

**This rule applies to ALL Mintlify components:** `<Accordion>`, `<Steps>`, `<Step>`, `<Tip>`, `<Warning>`, `<Card>`, `<Note>`, `<Info>`, `<AccordionGroup>`, `<CardGroup>`

## 2. Quote nesting in JSX attributes

Component attributes like `title="..."` are evaluated as JSX. If the value contains double quotes, the outer attribute can't also use double quotes — that breaks the JSX string and throws a `JSX expected a closing tag` error.

Wrong:
```mdx
<Accordion title="What is the "Closure" concept?">
```

Right (use single quotes for the outer attribute):
```mdx
<Accordion title='What is the "Closure" concept?'>
// or swap them
<Accordion title="What is the 'Closure' concept?">
```

**Special case:** If the title contains both single and double quotes, use HTML entities:
```mdx
<Accordion title="What is the &quot;Closure&quot; concept?">
```

## 3. Escape angle brackets in plain text

MDX parses a bare `<` as the start of a JSX tag. If it doesn't find a matching closing tag, the compiler crashes. Use HTML entities or inline code instead.

Wrong:
```mdx
When the main thread block time is > 16.6ms, frames will drop.
```

Right:
```mdx
When the main thread block time is &gt; 16.6ms, frames will drop.
// or wrap in backticks
When the main thread block time is `> 16.6ms`, frames will drop.
```

**Common patterns to watch for:**
- `< 25%` → `&lt; 25%` or `< 25%`
- `> 16.6ms` → `&gt; 16.6ms` or `> 16.6ms`
- `2^n` → `2^n` (in code blocks is fine)

## 4. Don't indent with 4 spaces inside components

Standard Markdown treats 4-space indentation as a code block. If you indent text inside an `<Accordion>` by 4 spaces, the parser treats the closing `</Accordion>` as part of the code block and leaves the component unclosed.

Wrong:
```mdx
<Accordion title="Deep Dive">

    (4 spaces here) This is the first paragraph.
</Accordion>
```

Right — don't indent inner text at all. For quoted content, use `> ` without leading spaces:
```mdx
<Accordion title="Deep Dive">

> This is the first paragraph.

</Accordion>
```

For nested lists, use at most 2 spaces.

## 5. Close all tags

MDX is JSX. Every tag needs a closing partner.

- Self-closing HTML tags need a trailing slash: `<br />`, not `<br>`. `<img />`, not `<img>`.
- Component tags must appear in pairs. No overlapping scopes.

## 6. Code block closing must NOT have trailing characters

The closing ``` of a code block must be on its own line with NO trailing characters. Any character after ``` (including `"`, `'`, `)`, `}`) will cause the parser to think the code block is not properly closed.

Wrong:
```mdx
    // code content
    ```"  ❌ The " after ``` causes parsing error
```

Wrong:
```mdx
    // code content
    ```  ❌ The  after ``` causes parsing error
```

Right:
```mdx
    // code content
    ```  ✅ No trailing characters
```

**This is the #1 cause of "Expected a closing tag for `<Accordion>`" errors.** Always check that code blocks are properly closed without any trailing characters.

## 7. Accordion titles with special characters

When Accordion titles contain special characters (like `?`, `!`, `:`, `+`, `-`), use single quotes for the outer attribute to avoid conflicts with JSX parsing.

Wrong:
```mdx
<Accordion title="1 + '1' 和 1 - '1' 的结果为什么不同?" icon="skull">
```

Right:
```mdx
<Accordion title="1 + '1' 和 1 - '1' 的结果为什么不同?" icon="skull">
```

**Rule of thumb:** If the title contains single quotes, use double quotes for the outer attribute. If it contains double quotes, use single quotes.

## 8. Don't use `sed` or batch tools to fix MDX files

Never use `sed`, `awk`, or other batch text processing tools to fix Mintlify MDX parsing errors. These tools can introduce duplicate blank lines or other formatting issues that cause new parsing errors.

**Always use the Edit tool for precise, single-point fixes.** This ensures you can see exactly what's being changed and avoid unintended side effects.

---

## Quick Checklist

Before committing MDX files, verify:

- [ ] All component tags have blank lines before and after content
- [ ] No bare `<` or `>` in text (use `&lt;`, `&gt;`, or backticks)
- [ ] Code block closing ``` has NO trailing characters
- [ ] Accordion/Tip/Warning titles don't have nested quote issues
- [ ] No 4-space indentation inside components
- [ ] All tags are properly closed

---

Breaking any of these will crash `npx mintlify dev` or throw a 500 on the page.

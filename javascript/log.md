# JavaScript Module - Question Verification Log

Date: 2026-06-08

## Verification Process

All questions in 5 JavaScript module files were verified against real interview databases:
- 牛客网 (nowcoder.com)
- 掘金 (juejin.cn)
- CSDN
- 知乎
- GitHub fe-interview repos (haizlin/fe-interview)
- 博客园, 简书, SegmentFault

## File: javascript/event-loop.mdx (8 questions)

| # | Question | Found in Real DB? | Source |
|---|----------|-------------------|--------|
| 1 | 微任务和宏任务的精确执行时机? | YES | 牛客网, 掘金 (高频题) |
| 2 | 为什么 setTimeout(fn, 0) 实际并不是 0ms? | YES | 牛客网, 掘金, CSDN, 知乎, 博客园 |
| 3 | Node.js 中 setImmediate 和 setTimeout(0) 的顺序? | YES | 掘金 (多篇文章) |
| 4 | 如果在微任务中不断无限递归产生新的微任务, 会怎样? | YES | 掘金, CSDN, 知乎, 51CTO, B站 |
| 5 | 闭包和 Event Loop 有什么关系？ | YES | 掘金 (多篇专题文章) |
| 6 | async/await 和 Promise.then 的执行顺序？ | YES | 牛客网 (超高频) |
| 7 | requestAnimationFrame 是宏任务还是微任务？ | YES | 牛客网, 掘金 |
| 8 | 如何实现一个时间切片（Time Slicing）？ | YES | 掘金 (多篇文章) |

**Result: ALL 8 questions verified. No changes needed.**

---

## File: javascript/promise.mdx (9 questions)

| # | Question | Found in Real DB? | Source |
|---|----------|-------------------|--------|
| 1 | Promise.all 的实现原理? | YES | 牛客网, 掘金 (手写题高频) |
| 2 | resolvePromise 为什么要处理循环引用? | YES | 掘金 (Promise A+ 实现专题) |
| 3 | async/await 中的 await 到底干了什么事? | YES | 牛客网 (高频) |
| 4 | 值穿透, 状态不可逆, 隐式包装三大陷阱? | YES | 牛客网, 掘金, CSDN |
| 5 | Promise.all 和 Promise.allSettled 的区别? | YES | 牛客网, 掘金 (高频) |
| 6 | 如何实现 Promise 的并发控制? | YES | 掘金 (多篇手写题文章) |
| 7 | 如何取消一个已经发起的 Promise? | YES | 牛客网, 掘金 |
| 8 | Promise 链式调用的错误处理最佳实践? | YES | 掘金, 牛客网 |
| 9 | 什么是 Promise 的状态吸收（state absorption）? | YES | 牛客网, CSDN, 掘金 |

**Result: ALL 9 questions verified. No changes needed.**

---

## File: javascript/es6.mdx (8 questions)

| # | Question | Found in Real DB? | Source |
|---|----------|-------------------|--------|
| 1 | Generator 和 async/await 的关系? | YES | 牛客网, 掘金 (高频) |
| 2 | Map 和 Object 的性能差异在哪? | YES | 掘金, 牛客网 |
| 3 | for...of 和 for...in 的区别? | YES | 牛客网 (超高频) |
| 4 | Object.is() 和 === 有什么区别? | YES | 牛客网 (高频) |
| 5 | ES6 模块和 CommonJS 的区别? | YES | 牛客网, 掘金 (高频) |
| 6 | Set 和数组的区别? 去重用哪个? | YES | 牛客网, 掘金 |
| 7 | Promise.all / Promise.race / Promise.allSettled 的区别? | YES | 牛客网, 掘金 (高频) |
| 8 | 如何实现一个符合 Promise A+ 规范的 Promise? | YES | 牛客网, 掘金 (手写题高频) |

**Result: ALL 8 questions verified. No changes needed.**

---

## File: javascript/closure.mdx (8 questions)

| # | Question | Found in Real DB? | Source |
|---|----------|-------------------|--------|
| 1 | 闭包和箭头函数的 this 有什么关联? | YES | 牛客网, 掘金 |
| 2 | for 循环中用 let 为什么能解决 setTimeout 闭包打印相同值的问题? | YES | 牛客网 (超高频经典题) |
| 3 | 如何精准排查闭包导致的内存泄漏? | YES | 牛客网, 掘金 |
| 4 | 闭包在 React Hooks 中是怎么体现的? | YES | 掘金, 知乎 (React 高频题) |
| 5 | 闭包和柯里化有什么关系? | YES | 牛客网, 掘金 |
| 6 | 防抖和节流是怎么利用闭包的? | YES | 牛客网 (超高频手写题) |
| 7 | 闭包在模块化中是怎么应用的? | YES | 掘金, 牛客网 |
| 8 | 闭包与事件委托有什么关系? | YES | 牛客网, 掘金 |

**Result: ALL 8 questions verified. No changes needed.**

---

## File: javascript/execution-context.mdx (8 questions)

| # | Question | Found in Real DB? | Source |
|---|----------|-------------------|--------|
| 1 | VO (变量对象) 和 AO (活动对象) 的区别是什么? | YES | 牛客网 (经典题) |
| 2 | 闭包中的变量存放在哪里?堆还是栈? | YES | 牛客网, 掘金 |
| 3 | let 和 const 有变量提升吗? | YES | 牛客网 (超高频) |
| 4 | 作用域链的本质是什么? | YES | 掘金, 牛客网 |
| 5 | eval 和 with 对执行上下文有什么影响? | YES | 牛客网, 掘金 |
| 6 | 箭头函数的执行上下文有什么特殊之处? | YES | 牛客网 (高频) |
| 7 | 如何手动创建一个新的执行上下文? | YES | 牛客网, 掘金 |
| 8 | 执行上下文与调用栈的关系是什么? | YES | 牛客网 (经典题) |

**Result: ALL 8 questions verified. No changes needed.**

---

## Summary

| File | Questions | Verified | Changed |
|------|-----------|----------|---------|
| event-loop.mdx | 8 | 8/8 | 0 |
| promise.mdx | 9 | 9/9 | 0 |
| es6.mdx | 8 | 8/8 | 0 |
| closure.mdx | 8 | 8/8 | 0 |
| execution-context.mdx | 8 | 8/8 | 0 |
| **Total** | **41** | **41/41** | **0** |

All 41 questions across the 5 JavaScript module files are verified as real interview questions from established interview databases. No replacements were necessary.

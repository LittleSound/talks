---
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# some information about your slides (markdown enabled)
title: 加入我们构建 Vue 高性能未来
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: fade-out
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
glowSeed: 200
css: unocss
---

<div fixed mt--35>
<div font-900 class="!text-50 op10">
💨 Vapor
</div>
</div>

# 加入我们构建 Vue 高性能未来

**探索 Vue Vapor，了解其原理，探索我们的最新进展，并学习如何做出贡献。**

<span bg-black:10 rounded px1 op75>
2025-01-03 🎄 Cat Home Demo
</span>

<!--
我想分享一下我的开源经历，以及最近在研究的一些东西。

演讲分成三个部份：
  1. 从框架作者的角度思考并介绍什么是 Vue Vapor。
  2. Vapor 的最新进展。
  3. 介绍我参与开源的经验。
-->

---
class: text-center
---

<div mt20 flex="~ col gap10">

# 🧪 思想实验：最快的框架

<v-click>

### 🧑‍💻 充满好奇心和想象力的前端程序员

</v-click>

<v-click>

### 💡 想发明更快的框架

</v-click>

</div>

<!--
[click] 想象一下你是一位前端程序员，作为一个充满好奇心和想象力的程序员，你喜欢探索新奇的想法。

[click] 你会问自己：有什么办法可以改进现有的前端框架的性能吗？

我不是想探讨如何发明 Vue Vapor 的真实过程，而是一个虚构的思维冒险。

-->

---
class: text-center
clicks: 2
---

### 🧪 思想实验：最快的框架

<v-click>

<div h20 />

<h1 op80> 前端框架的性能表现 </h1>

<div mt10 px10 flex flex-col gap2 relative>
  <div font-hand abs-tr top="-14" rotate-13 text-2xl>Longer is better!</div>
  <PerformanceProgress name="Vanilla JS" :progress="100" :highlight="$clicks >= 2" icon="i-logos:javascript" />
  <PerformanceProgress name="Vue vDOM" :progress="80.6" icon="i-logos:vue" />
  <PerformanceProgress name="React" secondary="Jotai" :progress="68" icon="i-logos:react" />
</div>

</v-click>

<!--
[click] 【看 PPT 上的图】所以让我们来看看前端框架的性能

想象一下如果我们想要在前端框架的性能表现中取得好的成绩，我们会怎么做？

我们会想性能列表中最好的家伙是谁？那就是那个基准，那个 1.0。它是怎么做的？

[click] 它是 Vanilla 的，也就是原生的 DOM 操作代码。它为什么能获得那么好的成绩？因为它足够灵活。编写它的人如果掌握了足够的优化技巧，他就可以根据这个测试去做很多的 “hacker 技巧” 来让性能表现更好。

-->

---

<!-- TODO: 增加更好的例子，可以查询相关的文章找一下 -->

<h1 class="!text-lg">Vanilla 中的优化技巧</h1>

<div flex gap10>
<div flex-1 of-hidden>

<h2 v-click class="!text-2xl mb-5">批量更新</h2>

<v-click>

🐌 不好的做法：频繁触发重排重绘

```javascript
items.forEach((item) => {
  container.style.width = `${tw += item.width}px`
  container.style.height = `${th += item.height}px`
})
```
</v-click>

<div h5 />

<v-click>

🥰 Vanilla 优化：收集更新后一次性应用

```javascript
const updates = items.reduce((acc, item) => {
  acc.width += item.width
  acc.height += item.height
  return acc
}, { width: 0, height: 0 })

container.style.cssText = `
  width: ${updates.width}px;
  height: ${updates.height}px;`
```

</v-click>

</div>
<div flex-1 of-hidden>

<h2 v-click class="!text-2xl mb-5">事件代理</h2>

<v-click>

🐌 不好的做法：给每个元素绑定事件

```javascript
items.forEach((item) => {
  item.addEventListener('click', handler)
})
```

</v-click>

<div h5 />

<v-click>

🥰 Vanilla 优化：使用事件代理

```javascript
container.addEventListener('click', (e) => {
  if (e.target.matches('.item')) {
    handler(e)
  }
})
```

</v-click>

</div>
</div>

<!--
我有两个例子：
1. 批量更新
2. 事件代理
-->

---
class: text-center
---

<div
  fixed inset-0 grid grid-cols-2 items-center justify-center font-900
  transition="all 0.3s"
  :class="{
    '!text-10 op100': [0].includes($clicks),
    '!text-25 op10': [1].includes($clicks),
  }"
>
  <div>
  模版复用
  </div>
  <div>
  事件代理
  </div>
  <div>
  批量更新
  </div>
  <div>
  响应式…
  </div>
</div>

<v-click>
  <div fixed inset-0 flex items-center justify-center>
    <h1 class="!text-15">⚙️ 编译器 Compiler</h1>
  </div>
</v-click>

<!--

我们还有很多优化的技巧，比如模版复用、响应式等等。

虽然直接使用原生 DOM API 编写上面这种代码确实很灵活，但是使用框架很明显给我带来了更好的开发体验和更低的上手门槛啊。

那这时我们作为想要开发出高性能框架的开发者，会怎么想呢。

[click] 我们知道有一个东西叫做编译器（Compiler）它可以把一种编码，我们称之为源码（source code）根据设定好的规则转换成另种编码，我们称之为运行时代码（runtime code）。
-->

---

<div fixed inset-0 flex="~ items-center justify-between gap10" p10>
  <div i-logos-vue text-100 op10 />
  <div i-logos-javascript text-100 op10 />
</div>

<div flex w-full justify-between op80>

<div flex="~ col justify-center items-center">

```vue
<script setup lang="ts">
import { ref } from 'vue'

const msg = ref('Hello World!')
</script>

<template>
  <h1>{{ msg }}</h1>
  <input v-model="msg">
</template>
```

</div>

<div flex="~ justify-center items-center">
<div i-lucide-arrow-big-right class="text-20" />
</div>

<div flex="~ col">

```javascript
const __sfc__ = defineComponent({
  vapor: true,
  setup(__props) {
    const msg = ref('Hello World!')

    return { msg }
  }
})

const t0 = _template('<h1></h1>')
const t1 = _template('<input>')
function render(ctx, $props, $emit, $attrs, $slots) {
  const n0 = t0()
  const n1 = t1()
  withDirectives(n1, [[_vModelText, () => ctx.msg]])
  delegate(n1, 'update:modelValue', () => $e => (ctx.msg = $e))
  renderEffect(() => setText(n0, (ctx.msg)))
  return [n0, n1]
}
__sfc__.render = render
__sfc__.__file = 'src/App.vue'
export default __sfc__
```
</div>

</div>

<!--
那如果我们编写一个足够智能的编译器，它能把你写的框架内代码，比如 .vue 文件。编译成浏览器原生的 DOM 操作。并且它知道如何使用这些““hacker 技巧”去优化性能。那我们的框架就能在跑分种获得与 Vanilla 接近的性能表现。

这就是 Vue Vapor 原理和核心思想。
-->

---
class: text-center
---

<div h-50vh flex items-center justify-center>
  <h1 class="!text-15">🍳 Vapor 的现状</h1>
</div>

<!--

下面让我们来了解一下 Vapor 的现状。

TODO：更详细的介绍 Vapor 的现状。
-->

---
class: text-center
---

<h1>Vapor 的性能</h1>

<div mt10 px10 flex flex-col gap2 relative>
  <div v-click="4" font-hand abs-tr top="-14" rotate-13 text-2xl>Longer is better!</div>
  <PerformanceProgress v-click name="Vanilla JS" :progress="100" icon="i-logos:javascript" />
  <PerformanceProgress v-click="4" name="Vue Vapor" :progress="90" icon="i-logos:vue" highlight />
  <PerformanceProgress v-click="3" name="Vue vDOM" :progress="80.6" icon="i-logos:vue" />
  <PerformanceProgress v-click="2" name="React" secondary="Jotai" :progress="68" icon="i-logos:react" />

  <p mt10="!" text-xs op60 v-click="4">
  * <a href="https://x.com/sanxiaozhizi/status/1842807976157155432/photo/1" target="_blank">The results</a> are based on <a href="https://github.com/krausest/js-framework-benchmark" target="_blank">js-framework-benchmark</a>, and tested on a MacBook Pro M1 Max.
  </p>

</div>

<!--

【展示 Vapor 的性能表现，逐一点击展示数据】

下面我们来看看 Vapor 的性能：

[click] 首先，我们有 Vanilla JS，它是速度的黄金标准，所以是 100 分，满分。

[click] 然后是 React，它的性能表现是 68 分。

[click] Vue vDOM，它的性能表现是 80.6 分。

[click] 最后是 Vue Vapor，它的性能表现是 90 分。

如果我们把 VanillaJS 的在跑分中的性能表现作为 💯 一百分的话，Vapor 现在的性能表现已经达到了 90 分水平了。

关于 Vapor 现状的信息我就先浅浅的分享到这里。我们最近还在进行一次大重构，它会让 Vapor 的性能更上一层楼，期待之后能和你们更详细的分享。

讲了这么多，我想你们也会对这个项目有了一些兴趣。Vapor 作为一个正在开发中的项目也会需要很多的来自社区的力量的帮助。所以接下我们来讲述一下我参与开源以来的经验，希望能帮到对开源感兴趣的伙伴，无论是对 Vapor 这个项目或者是别的开源项目。

-->

---
class: text-center
---

<div h-50vh flex flex-col items-center justify-center gap10>
  <h1 class="!text-15">🙌 无从下手的开源</h1>

<v-click>

秘籍：

### 1. 如何选择开源项目

</v-click>

<v-click>

### 2. 如何开始参与贡献

</v-click>

</div>

<!--

# 🙌 无从下手的开源

> 当我最开始遇到这个问题时我的想法是：我不知道怎么给一个开源项目做贡献。

我把这个问题分成两个部份

[click] 1. 如何选择项目。
[click] 2. 如何开始贡献。

-->

---
class: text-center
---

<div h-50vh flex flex-col items-center justify-center gap10>
  <h1 class="!text-15">👀 如何选择开源项目</h1>

<v-click>

### 兴趣是最好的老师

</v-click>

<v-click>

### 成熟项目的挑战

</v-click>

<v-click>

### 新生项目的机会

</v-click>

</div>

<!--

> 选择你感兴趣并且正在积极开发中的新开源项目。

我会分享一些开源的经验，关于如何开始和继续。主要是我对于自己开源经历的总结，它未必是完全正确的。

[click] 我第一次参与开源时。面对舒适圈外的世界，兴趣无意是我最好的老师和充沛动力的来源。所以请至少确保选择的项目是自己感兴趣的。

[click] 基于兴趣的基础上。如果打算贡献的是稳定成熟的开源项目。有些挑战是我们会面对的。我通常需要把我的更改写的非常完美，为此我需要了这个解项目的许多上下文。甚至是生态链下游的信息，也就是项目的用户在怎么使用它。而且整个社区中有很多人比我要了解这些的多。
所哟我的 PR 有可能会需要一两年才能被合并。维护者为了小心的避免破坏性更新需要仔细审阅每个 PR，而且这样的项目往往有很多 PR 等待被合并，而核心维护者只有两三个人。所以我们贡献这样的项目时要等那么久也就不足为奇了。

[click] 相比之下贡献与这个感兴趣的项目社区有关的正在积极开发中的新项目是一个更好的选择，它基本上没有什么包袱需要去担心破坏性更新影响到大量的用户，即使我的 PR 不是那么完美，通常也能被合并。这样的项目也伴随者更频繁的重构，所以比我更了解这个项目的人实际上也没有和我有非常巨大的差距。

-->

---
class: text-center
---

<div h-50vh flex items-center justify-center>
  <h1 class="!text-15">如何开始参与贡献</h1>
</div>

<!--
正在开发中的项目当然也包含许多未完成的工作或者待修复的 BUG，它们中有很多十分明显并且轻松就能完成。下面我会说一下如何开始这个过程并一步一步的深入。
-->

---

### 如何开始参与贡献

<div h10 />

<div grid grid-cols-2 gap10>

<div v-click of-hidden bg-gray:50 rounded-xl px10 py5 border flex items-center>

<h1 class="!m0 !p0">🧪 test</h1>

</div>

<div v-click of-hidden bg-gray:50 rounded-xl px10 py5 border flex items-center>

<h1 class="!m0 !p0">🐞 fix</h1>

</div>

<div v-click of-hidden bg-gray:50 rounded-xl px10 py5 border flex items-center>

<h1 class="!m0 !p0">🚀 feat</h1>

</div>

<div v-click of-hidden bg-gray:50 rounded-xl px10 py5 border flex items-center>

<h1 class="!m0 !p0">🧠 idea</h1>

</div>

<div v-click of-hidden col-span-2 bg-gray:50 rounded-xl px10 py5 border flex items-center>

<h1 class="!m0 !p0">💞 你的时间和你舒适的方式</h1>

</div>
</div>

<!--

TODO: 使用阶梯状的图表来展示这个过程

### 如何开始参与贡献

[click] test: 开始参与一个正在积极开发中的项目的贡献的一个很好的切入点是给这个项目补全单元测试。

正在开发中的项目的单元测试往往只包含了那些最基础的用例，如果去读一读这些测试，我们通常会发现一切需要补充的部份。有时候直接在项目中搜索 `TODO` 也是一个不错的选择。

在阅读旧的单元测试和尝试编写更详细的单元测试的过程中，我们会发现这个项目更深层次如何工作的原理。最开始的时候我们可能只是提交一些基础的单元测试补全 PR，因为我们还没有搞明白怎么修复那些坏掉的测试，没关系我们可以在 PR 里面标记那些测试是失败的。这样社区里的其他人就知道这里有问题了，并且会试着去修复它。

[click] fix: 随着我们的积累，我们会发现一些感觉好像知道如何修复的单元测试用例。这个时刻通常很快就会到来，不要担心犯错。这时我们已经开始参与功能的改进了，而不只是补充单元测试。随着我们的积累，会对这个过程越来越熟练。

[click] feat 到这时，项目的其他贡献者和主要的维护者会熟悉你的存在。如果维护者决定添加一个新功能，我们会有把握说，”我想尝试一下实现这个“，还是那句话：“不要担心犯错或失败”。到了这个阶段，你已经开始参与新功能的开发了。

[click] idea 随着我们对项目理解的深入和因为你在社区中贡献而被其他开发者所熟知。我们将会不只是提供自己编写的代码，也包括我们的想法，然后我们的想法会被其它活跃的贡献者所实现。到了这时候你已经成为这个项目里重要的一员了。

[click] 你的时间和你舒适的方式

做上述这些事情无疑是非常消耗时间的，越深入这个社区就越是如此。取决于我们有多少时间和你喜欢的舒适的方式，我们可以在这个光谱的任何地方停下来，并享受那种程度的开源之旅。

-->

---
layout: center
class: 'text-center pb-5'
---

# 谢谢！

幻灯片可在 [github.com/LittleSound/talks](https://github.com/LittleSound/talks) 查看与下载

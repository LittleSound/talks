---
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# some information about your slides (markdown enabled)
title: Vapor 和我的开源之旅
info: |
  从 Vue Vapor 贡献者的视角，分享参与 Vue 开源项目的经历与感悟
  Author: Rizumu Ayaka (@LittleSound)
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

<h1 class="!text-12">Vapor 和我的开源之旅</h1>

**从 Vue Vapor 贡献者的视角，分享参与 Vue 开源项目的经历与感悟**

<span bg-black:10 rounded px1 op75>
VueConf 深圳 2025
</span>

<div fixed bottom-10 right-10 flex justify-center text-sm op75>

Create your own slides like this: [<div i-ri:github-fill inline-block /> littlesound/talks-template](https://github.com/LittleSound/talks-template)

</div>

<!--
很高兴今天能在这里和大家做这个关于 Vapor 的分享。

感谢 VueConf 深圳能给我这次机会。
-->

---
layout: intro
class: pl-30
glowSeed: 14
---

# LittleSound｜Rizumu

<div class="[&>*]:important-leading-10 opacity-80">

team member of {Vue} {Elk} and developing {Vapor}<br>
Creator of {Nolebase} {InterlineTranslate} {SlimeForm} {Guii.AI}<br>

</div>

<div my-10 w-min flex="~ gap-1" items-center justify-center>
  <div i-ri-github-line op50 ma text-xl ml4/>
  <div><a href="https://github.com/LittleSound" target="_blank" class="border-none! font-300">LittleSound</a></div>
  <div i-ri-twitter-x-line op50 ma text-xl ml4/>
  <div><a href="https://x.com/OikawaRizumu" target="_blank" class="border-none! font-300">OikawaRizumu</a></div>
  <div i-ri-bluesky-line op50 ma text-xl ml4 />
  <div><a href="https://bsky.app/profile/rzmu.bsky.social" target="_blank" class="border-none! font-300">rzmu.bsky.social</a></div>
</div>

<img src="https://github.com/LittleSound.png" rounded-full w-40 abs-tr mt-16 mr-12/>

<div flex="~ gap2">

</div>

<!--
OK。首先，自我介绍一下。

我叫小音，我 GitHub 上的 ID 是 LittleSound。

我是一名热爱开源的独立开发者。同时也是 Vue Vapor 团队的一员。

-->

---

## 🍪 小饼干

<div flex flex-wrap max-w-100vh max-h-100vh justify-between gap-10>
  <img flex-1 max-w-40vh max-h-40vh src="/饼干-主图.png" />
  <img flex-1 max-w-40vh max-h-40vh src="/饼干-配件.png" />
  <img flex-1 max-w-40vh max-h-40vh src="/饼干-物料.png" />
</div>

<!--
除了 Vue 之外，我最近还在玩 3D 打印。

今天我带了一些小饼干过来，分享给大家。

回到 Vapor。
过去一年多的时间中，我一直深度参与构建 Vue Vapor 这个令人兴奋的新功能。

嗯。所以让我们回到 Vapor 的话题。

-->

---
class: text-center
---

<div w-full h-full flex="~ col gap5 items-center justify-center">

<div font-900 class="!text-30">
<div i-logos-vue text-23 inline-block mr--3 />apor 💨
</div>

<v-click>

### Vapor Is No Virtual DOM

</v-click>

<v-click>

## 🧪 Thought Experiment: Faster Framework

</v-click>

</div>

<!--
如果你对 Vapor 已经比较熟悉了，你可能会知道我要介绍说：

[click] Vapor 是没有 Virtual DOM 的 Vue，灵感来自 Solid。对吧？？

嗯…实际上我并不想这么介绍 Vapor，因为它有点难懂，所以让我们换一种方式。

[click] 首先让我们来假设一下，如果你是尤雨溪，你会怎么改进如今前端框架的性能？
-->

---
class: text-center
clicks: 4
---

### 🧪 Thought Experiment: Faster Framework

<v-click>
  <div h20 />

  <h1 op80>Performance</h1>

  <div mt10 px10 flex flex-col gap2 relative>
    <div font-hand abs-tr top="-14" rotate-13 text-2xl>Longer is better!</div>
    <PerformanceProgress v-click="4" name="Vanilla JS" :progress="100" highlight icon="i-logos:javascript" :interval="[0,100]" />
    <PerformanceProgress v-click="3" name="Vue vDOM" :progress="79" icon="i-logos:vue" :interval="[0,100]" />
    <PerformanceProgress v-click="2" name="React" secondary="Jotai" :progress="63" icon="i-logos:react" :interval="[0,100]" color-class="bg-gradient-from-yellow-700 bg-gradient-to-yellow-300 bg-gradient-to-rt" />
  </div>
</v-click>

<!--
这样吧，[click] 让我们从前端框架如今的性能排名开始讲起：

首先是 React，[click] 它的性能表现是 63 分。

关于性能优化你会想到什么办法呢？继续用 Virtual DOM，然后做更多的优化？如果你看过尤雨溪以前的一些 Talk，你可能会知道，是的。Vue 已经在 Virtual DOM 上加了大量的优化了。

[click] 所以如今 Vue 在这里，它是 79 分。

如果你还想更快，你会怎么做呢，你会怎么解决这个问题？

你可能会想性能列表中最好的家伙是谁？它是怎么做的？

[click] 那个家伙就是 Vanilla JS，它是这个排名的满分标准，所以它是 100分。

Vanilla 的意思是香草，也就是我们吃的冰淇淋的"原味"。

所以 Vanilla 是原生的 DOM 操作代码，是的。它直接操作 DOM 本身，没有 Virtual DOM。
-->

---

<h1 class="!text-lg">Hacky tricks in Vanilla</h1>

<div flex gap10>
<div flex-1 of-hidden>

<h2 v-click class="!text-2xl mb-5">Batch updates</h2>

<v-click>

🐌 Bad: forEach update

```javascript
items.forEach((item) => {
  container.style.width = `${tw += item.width}px`
  container.style.height = `${th += item.height}px`
})
```
</v-click>

<div h5 />

<v-click>

🥰 Improved: Reduced updates

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

<h2 v-click class="!text-2xl mb-5">Event delegation</h2>

<v-click>

🐌 Bad: forEach event listener

```javascript
items.forEach((item) => {
  item.addEventListener('click', handler)
})
```

</v-click>

<div h5 />

<v-click>

🥰 Improved: event delegation

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
它为什么那么快？ 因为它足够灵活。编写它的人如果掌握了足够的优化技巧，他就可以根据这个测试去做很多的 "hacker 技巧" 来让性能表现更好。

让我们看几个例子。

[click] 比如"批量更新"

[click] 那我们先来看一个不好的做法，不好的做法就是，比如说你要改一个元素的宽高，但是你可能会有好几个值。那么你可能会这样写，每次改一个值，然后就会触发一次重排重绘。那这样就会非常的慢。

[click] 更好的做法是，你可以先收集所有的更新，然后一次性应用。

[click] 还有一个例子是"事件代理"

[click] 举个例子。不好的做法是我有一个列表，列表有一万行。那我每个条目都要有一个删除操作。那我就挂一万个事件。这样会非常慢。

[click] 更好的做法是我在这个列表顶层的元素上挂一个事件，然后我去看触发这个事件的是哪个元素，然后去处理它。这样我就只要挂一个事件，所以这样也会更快。

我们还有很多优化的技巧，[click] 比如模版复用、响应式编程之类的都可以去提升它的性能。
-->

---
class: text-center
clicks: 2
---

<div
  fixed inset-0 grid grid-cols-2 items-center justify-center font-900
  transition="~ 500 ease"
  :class="{
    '!text-8 op100': [0].includes($clicks),
    '!text-8 op10': [1].includes($clicks),
    '!text-10 op10': [2].includes($clicks),
  }"
>
  <div>
    Advanced<br>
    Optimization
  </div>
  <div>
  DOM Reuse
  </div>
  <div>
  Batch Update
  </div>
  <div>
  Fine-grained<br>
  Reactivity
  </div>
</div>

<v-switch unmount>
  <template #1>
    <div
      fixed inset-0 flex="~ items-center justify-center"
      v-motion
      :initial="{ scale: 0, opacity: 0 }"
      :enter="{ scale: 1, opacity: 1 }"
      :leave="{ scale: 0, opacity: 0 }"
    >
      <div i-logos-vitejs text-50 />
    </div>
  </template>
  <template #2>
    <div fixed inset-0 flex items-center justify-center>
      <h1
        class="!text-15 font-900"
        v-motion
        :initial="{ scale: 0, opacity: 0 }"
        :enter="{ scale: 1, opacity: 1 }"
        :leave="{ scale: 0, opacity: 0 }"
      >
        ⚙️ Compiler
      </h1>
    </div>
  </template>
</v-switch>

<!--
所以我们实际上不需要 Virtual DOM 对吧？

但是有时候直接使用原生 DOM API 很麻烦，你要学很多技巧。而且你还要考虑怎么和你的同事合作。

那我们用框架。但是这个问题应该怎么解决呢？

实际答案就在我们身边，[click] 答案在 Vite 里。

我们已经很久不直接编写 DOM API 了，我们也不直接编写实际运行的 JS 对吧，我们实际上都会装一个 Vite 来帮我们。

[click] 因为在这背后，我们知道有一个东西叫做编译器（Compiler）
-->

---
class: text-center
clicks: 3
---

### ⚙️ Compiler

<div fixed inset-0 flex="~ items-center justify-center gap10" p10>
  <div v-click="1" i-logos-vue text-50 />
  <div v-click="2" flex="~ justify-center items-center">
    <div i-lucide-arrow-big-right class="text-20" />
  </div>
  <div v-click="3" i-logos-javascript text-50 />
</div>

<!--
它可以把源码，[click] 比如 vue 文件，根据你设定好的规则 [click] 转换成另种我们称之为 [click] 运行时代码（runtime code）的代码。
-->

---
class: text-center
---

### ⚙️ Compiler

<div fixed inset-0 flex="~ items-center justify-center gap10" p10>
  <div i-logos-vue text-50 />
  <div flex="~ justify-center items-center">
    <div i-lucide-arrow-big-right class="text-20" />
  </div>
  <div>
    <div i-logos-javascript text-50 relative />
    <div text-6 mt2>
      <div absolute z-10 v-click v-click.hide>with Virtual DOM</div>
      <div absolute z-10 v-click>with Real DOM</div>
    </div>
  </div>
</div>

<!--
实际上，在 Vue 中，我们一直都在使用这种方式编译 [click] Virtual DOM 运行时。

但是像我之前说的，Virtual DOM 运行时离真实 DOM 操作太远了。

它不容易改变，而且每次重新渲染，额外的工作都会运行，无论你需不需要。

所以我们想使用编译器，但是去掉 Virtual DOM，然后使用编译器来 [click] 直接构建 DOM 操作。
-->

---
class: text-center
clicks: 2
---

### ⚙️ Compiler

<div fixed inset-0 flex="~ items-center justify-between gap10" p10 mt7>
  <div v-click="1" i-logos-vue text-100 op10 />
  <div v-click="2" i-logos-javascript text-100 op10 />
</div>

<div flex w-full justify-between op80 text-left mt7>

<div v-click="1" flex="~ col justify-center items-center">

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
<div v-click="2" i-lucide-arrow-big-right class="text-20" />
</div>

<div  v-click="2" flex="~ col">

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
所以，回到 Vapor。如果我们做一个足够聪明的编译器。

[click] 它可以拿一个 Vue SFC 文件，[click] 编译成原生 DOM 操作。

而且它知道如何使用这些 "hacker 技巧" 来优化性能。

所以我们的框架可以在基准测试中达到接近原生的性能。

这就是 Vapor 的全部基础。
-->

---

<div size-full text="!20" font-500 flex="~ col items-center justify-center">
  <h1
    text="!1em" absolute
    transition="~ duration-500 ease-in-out"
    :class="{
      'translate-y--20 scale-35 op80': $clicks > 0,
    }"
  >🎉 Congratulate</h1>
  <v-click>
    <h1 text="!1em" absolute>You invented Vapor</h1>
  </v-click>
</div>

<!--
So... Congratulations, [click] You invented Vapor.
-->

---

<div
  style="background-image: url(https://contrib.rocks/image?repo=vuejs/vue-vapor)"
  fixed inset-0 z0 :class="{ 'op35': $clicks > 0 }"
  transition="~ duration-500 ease-in-out"
/>

<div z10 fixed inset-0 flex="~ col justify-center items-center">
  <v-click>
    <h1
      absolute text="!20" font-800
      transition="~ duration-500 ease-in-out"
      :class="{
        'translate-y--30 scale-35 op80': $clicks > 1,
      }"
    >
      Contributors
    </h1>
  </v-click>
</div>

<!--
以上所有的这一切功能和愿景都离不开 [click] Vue 社区的每一位贡献者。我想在这里感谢他们的付出。
-->

---

<div fixed inset-0 flex="~ col items-center justify-center">
  <h1
    absolute
    :class="{
      'scale-200 left-1/2 top-1/2 translate-x--1/2 translate-y--1/2': $clicks === 0,
      'scale-100 left-10 top-10 op80': $clicks > 0,
    }"
    transition="all duration-400 ease-in-out"
  >
    My Way to Open Source
  </h1>
</div>

<div size-full flex="~ items-center justify-center">
  <div flex="~ justify-center gap10">
    <v-click>
      <div
        v-motion :initial="{ y: 80, op: 0 }" :enter="{ y: 0, op: 1, transition: { delay: 250 } }"
        flex="~ 1 col" rounded-xl bg-gray:50 text-center bg="green/20" border="~ green"
      >
        <!-- icon -->
        <div class="text-20">❤️‍🔥</div>
        <div flex-1 bg="green/10" p3 rounded-xl>
          Interest is the best teacher
        </div>
      </div>
    </v-click>
    <v-click>
      <div
        v-motion :initial="{ y: 80 }" :enter="{ y: 0 }"
        flex="~ 1 col" rounded-xl bg-gray:50 text-center bg="green/20" border="~ green"
      >
        <!-- icon -->
        <div class="text-20">⏳</div>
        <div flex-1 bg="green/10" p3 rounded-xl>
          Bigger projects requires more work and time
        </div>
      </div>
    </v-click>
    <v-click>
      <div
        v-motion :initial="{ y: 80 }" :enter="{ y: 0 }"
        flex="~ 1 col" rounded-xl bg-gray:50 text-center bg="green/20" border="~ green"
      >
        <!-- icon -->
        <div class="text-20">🍀</div>
        <div flex-1 bg="green/10" p3 rounded-xl>
          New projects are full of chances
        </div>
      </div>
    </v-click>
  </div>
</div>

<!--
回想我最初参与 Vapor 的贡献。那天我在推特上看到了 Kevin Deng 说：有人要来一起写 Vue Vapor 吗？如果你过来找我的话，我可以教你。

实际上我当时完全不知道 Vapor 是什么，但是我对 Vue 很感兴趣。

嗯… 所以我买了第二天的车票。

从那边回来之后，我看了一晚上 Vapor 的代码都没看懂。我哭了，感觉自己完全搞不明白。但是我第二天又看了好多遍，终于搞懂了。

不过。如今我已经为 Vapor 贡献了许多代码。

所以…… 第一次参与开源时，离开了舒适圈，[click] 兴趣无疑是最好的老师和充沛动力的来源。

实际上我后面也有给 Vue Core 提交 PR。

那个 PR 大概花了一年才被合并。相同的 PR 在 Vue Vapor 里面大概一两天就被合并了。

实际上维护者为了小心的避免破坏性更新需要仔细审阅每个 PR，而且这样的项目往往有很多 PR 等待被合并，而核心维护者只有两三个人。

[click] 所以我们贡献这样的项目时要等那么久也就不足为奇了。

相比之下贡献像是 Vapor 这样你感兴趣的社区中的正在积极开发中的新项目是一个更好的选择。

[click] 它合并 PR 更快，经常被重构，而且有更多的机会。

比如未完成的功能或者待修复的 BUG，它们中有很多十分明显并且轻松就能发现并完成。
-->

---
class: text-center
---

<h1 fixed top-10 left-10 op80>My way to Open Source</h1>

<div size-full flex="~ col items-center justify-center gap10">
  <h1 class="!text-15">Where to start contribute?</h1>
</div>

<!--
实际上，就算这样。即使我读了一晚上的 Vue Vapor 的代码，在我去找 Kevin Deng 的时候，我也完全不知道我应该做什么，Kevin Deng 也想了很久。我那时关于 Vapor 几乎什么都不会。
-->

---

<h3 fixed top-10 left-10>Where to start contribute?</h3>

<div size-full flex="~ col justify-center gap10">
  <div flex="~ gap10">
    <v-click>
      <div
        v-motion :initial="{ y: 80 }" :enter="{ y: 0 }"
        flex="~ 1 col" rounded-xl text-center bg="green/20" border="~ green"
      >
        <!-- icon -->
        <div class="text-20">🧪</div>
        <div flex-1 bg="green/10" p3 rounded-xl>
          test
        </div>
      </div>
    </v-click>
    <v-click>
      <div
        v-motion :initial="{ y: 80 }" :enter="{ y: 0 }"
        flex="~ 1 col" rounded-xl text-center bg="green/20" border="~ green"
      >
        <!-- icon -->
        <div class="text-20">🐞</div>
        <div flex-1 bg="green/10" p3 rounded-xl>
          fix
        </div>
      </div>
    </v-click>
    <v-click>
      <div
        v-motion :initial="{ y: 80 }" :enter="{ y: 0 }"
        flex="~ 1 col" rounded-xl text-center bg="green/20" border="~ green"
      >
        <!-- icon -->
        <div class="text-20">🚀</div>
        <div flex-1 bg="green/10" p3 rounded-xl>
          feat
        </div>
      </div>
    </v-click>
    <v-click>
      <div
        v-motion :initial="{ y: 80 }" :enter="{ y: 0 }"
        flex="~ 1 col" rounded-xl text-center bg="green/20" border="~ green"
      >
        <!-- icon -->
        <div class="text-20">🧠</div>
        <div flex-1 bg="green/10" p3 rounded-xl>
          idea
        </div>
      </div>
    </v-click>
  </div>
  <v-click>
    <div
      v-motion :initial="{ y: 80 }" :enter="{ y: 0 }"
      of-hidden col-span-2 bg-pink:20 rounded-xl px10 py5 border="~ pink" flex items-center
    >
      <h1 class="!m0 !p0">💞 Your time and your comfortable way</h1>
    </div>
  </v-click>
</div>

<!--
那天 Kevin Deng 和我讲了不少，但是那点时间很难搞清楚那些深奥的知识，我现在还记得最清楚的事情是：
[click] 我可以帮忙写一些单元测试。

因为即使不会修复那些坏掉的测试，也没关系的。你可以在 PR 里面标记那些测试是失败的。这样社区里的其他人就知道这里有问题了。

并且在阅读旧的单元测试和尝试编写新单元测试的过程中，我发现了这个项目更深层次如何工作的原理。

然后，我回去后的第二天。我发现一个坏掉的测试，它非常简单的，我似乎明白怎么修复它。我决定提交一个修复的 PR [click]。

这就是写单元测试的好处。你很快会发现一些感觉好像知道如何修复的单元测试用例。

不要担心犯错。这时我们走出了新的一步：fix。

如果你坚持做，你会对这个过程越来越熟练。

并且到这时，项目的其他贡献者和主要的维护者会熟悉你的存在。如果维护者决定添加一个简单的新功能，你会有把握地说:

[click] "我想尝试一下实现这个"，还是那句话："不要担心犯错或失败"。到了这个阶段，你已经开始参与新功能的开发了。

随着你对项目理解的深入和因为你在社区中贡献而被其他开发者所熟知。你将会不只是提供自己编写的代码。

[click] 也包括你的想法，然后你的想法会被其它活跃的贡献者所实现。到了这时候你已经成为这个项目里重要的一员了。

做上述这些事情无疑是非常消耗时间的，越深入这个社区就越是如此。

[click] 取决于你有多少时间和你喜欢的舒适的方式，你可以在这个光谱的任何地方停下来，并享受那种程度的开源之旅。
-->

---

<div
  style="background-image: url(https://contrib.rocks/image?repo=vuejs/vue-vapor)"
  fixed inset-0 z0 :class="{ 'op35': true }"
  transition="~ duration-500 ease-in-out"
/>

<div z10 fixed inset-0 flex="~ col justify-center items-center">
  <h1
    absolute text="!20" font-800
    transition="~ duration-500 ease-in-out"
    :class="{
      'translate-y--20 scale-35 op80': $clicks > 0,
    }"
  >
    Contributors
  </h1>

  <v-click>
    <h1 class="font-800 !text-20">Join Us</h1>
      <div fixed bottom-10 flex items-center justify-center gap1 op80 text-xl>
        Recommended Reading:
        <div i-ri:github-fill />
        <a href="https://github.com/ubugeeei/reading-vuejs-core-vapor" target="_blank"><span op50>github.com/</span>ubugeeei/reading-vuejs-core-vapor</a>
      </div>
  </v-click>
</div>

<!--
这就是我的 Vapor 开源故事。

[click] 希望也能在这里看到你的故事。

【适当停顿】
-->

---

<div size-full flex="~ col items-center justify-center" font-500>
  <h1
    class="!text-15"
  >🍳 The status of Vapor</h1>
</div>

<!--
接下来。让我们来看看这样的架构给 Vue Vapor 带来了什么样的成果。
-->

---

<h3 fixed top-10 left-10 op75>
🍳 The status of Vapor
</h3>

<div size-full text="!15" font-500 flex="~ col items-center justify-center">
  <v-click>
    <h1
      text="!1em" absolute
      transition="~ duration-500 ease-in-out"
      :class="{
        'translate-y--20 scale-40': $clicks > 1,
      }"
    >
      Vapor is a subset of Vue
    </h1>
  </v-click>
  <v-click>
    <div scale-300>
```html
<script setup vapor />
```
    </div>
  </v-click>
</div>

<!--
首先，最重要的一点。

[click] Vapor 是 Vue 的子集。

所以只要打开一个开关 [click] 你不需要学习新的框架或者掌握复杂的技巧就能获得高性能。
-->

---
class: text-center
clicks: 2
---

<h1>Performance of Vapor</h1>

<div mt10 px10 flex flex-col gap2 relative>
  <TransitionGroup tag="div" name="list" class="relative flex flex-col gap2">
    <div v-click="2" :key="1" font-hand abs-tr top="-14" rotate-13 text-2xl>Longer is better!</div>
    <PerformanceProgress :key="2" v-click name="Vanilla JS" :progress="100" icon="i-logos:javascript" :interval="[0,100]" />
    <div :key="3" v-if="$clicks > 1">
      <PerformanceProgress name="Vue Vapor" :progress="93.4" icon="i-logos:vue" highlight :interval="[0,100]" />
    </div>
    <PerformanceProgress :key="4" v-click="1" name="Vue vDOM" :progress="79" icon="i-logos:vue" :interval="[0,100]" color-class="bg-gradient-from-lime-700 bg-gradient-to-lime-300 bg-gradient-to-rt" />
    <PerformanceProgress :key="5"  v-click="1" name="React" secondary="Jotai" :progress="63" icon="i-logos:react" :interval="[0,100]" color-class="bg-gradient-from-yellow-700 bg-gradient-to-yellow-300 bg-gradient-to-rt" />
  </TransitionGroup>

  <p mt10="!" text-xs op60 v-click="2">
  * The results are based on <a href="https://github.com/krausest/js-framework-benchmark" target="_blank">js-framework-benchmark</a>, and tested on Johnson's MacBook Pro.
  </p>

</div>

<!--
所以 Vapor 有多快？

[click] 如果我们说 VanillaJS 性能分数是 💯 一百，

[click] 那么 Vapor 现在的分数是 93.4 分。

这比 Virtual DOM 更快。
-->

---

<h1>Architecture</h1>

<Architecture />

<!--
并且由于 Vapor 编译器的 IR 架构。[click] 除了 `template` 语法，[click] 我们还可以从 JSX 编译到 Vapor 运行时。

感谢 Gao Fei (zhiyuanzmj) 添加了 JSX 特性！

还有很多特性，我这边就不一一列举了。
-->

---

# Recap

<v-clicks>

- We "invented" Vapor together.
- What is Vapor?
  - For better performance, Vapor builds native DOM operations based on the compiler. No Virtual DOM.
  - Vapor is a subset of Vue. They can work together.
  - Uses IR architecture, supports compiling JSX to Vapor runtime.
  - ...
- How to contribute?
  - Choose a project you're interested in.
  - Start with writing unit tests. Fix issues, propose new ideas, enjoy the open source journey.

</v-clicks>

<!--
所以... 今天,我们一起 [click] 发明了 Vapor。[click] 然后介绍了它的性能，它的架构，它的路线图，[click] 以及感谢了贡献者们，还听了我的开源故事。

以上就是这个演讲的全部啦。[click] 我为这次演讲练习了很多遍...

-->

---

# References

- Vue Vapor
  - [Vue Vapor](https://github.com/vuejs/vue-vapor)
  - [Slides: Vue Vapor: Reinvention](https://github.com/sxzz/talks/tree/main/2024-10-vue-fes-japan)
  - [Slides: Yak Shaving](https://talks.antfu.me/2024/vue-fes-japan/)
  - [Thinking Granular: How is SolidJS so Performant?](https://dev.to/ryansolid/thinking-granular-how-is-solidjs-so-performant-4g37)

- Talks
  - [iPhone 1 launch event speech](https://www.google.com/search?q=iPhone+1+launch+event+speech&sourceid=chrome&ie=UTF-8)

<div h-10 />

**Thank you, [Kevin Deng](https://github.com/sxzz) and [Anthony Fu](https://github.com/antfu).**

<!--
我为这次演讲练习了很多遍，查了很多资料。

所以… [click] 希望你会喜欢，也希望你能从中得到一些启发。

[click] 谢谢你的聆听。
-->

---
layout: center
class: 'text-center pb-5'
---

# Thanks！

<div op75>

**Slides can be found at [<div i-ri:github-fill inline-block /> LittleSound/talks](https://github.com/LittleSound/talks)**

Slides template at [<div i-ri:github-fill inline-block /> littlesound/talks-template](https://github.com/LittleSound/talks-template)

</div>

<!--
and Thank you for joining us.
-->

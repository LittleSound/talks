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

<h1 class="!text-12">Join Us Building Vue's Faster Future</h1>

**Discover Vue Vapor, understand it, catch up latest progress, and learn how to contribute.**

<span bg-black:10 rounded px1 op75>
Demo Inn 2025-01-18
</span>

<!--
Hello everyone. I’m so happy to be here today to share with you things about Vapor.

And again, I want to say thank you to Vue Nation, for giving me this opportunity while my English isn’t very good now.
-->

---
layout: intro
class: pl-30
glowSeed: 14
---

# 小音 LittleSound

<div class="[&>*]:important-leading-10 op80 blur-sm">

team member of {Vue} {Elk} and developing {Vapor}<br>
Creator of {Nolebase} {InterlineTranslate} {SlimeForm} {Guii.AI}<br>

</div>

<div my-10 w-min flex="~ gap-1" items-center justify-center blur-sm>
  <div i-ri-github-line op50 ma text-xl ml4/>
  <div><a href="https://github.com/LittleSound" target="_blank" class="border-none! font-300">LittleSound</a></div>
  <div i-ri-twitter-x-line op50 ma text-xl ml4/>
  <div><a href="https://x.com/OikawaRizumu" target="_blank" class="border-none! font-300">OikawaRizumu</a></div>
  <div i-ri-bluesky-line op50 ma text-xl ml4 />
  <div><a href="https://bsky.app/profile/rzmu.bsky.social" target="_blank" class="border-none! font-300">rzmu.bsky.social</a></div>
</div>

<div fixed top="1/2" text-15 font-900 op20>
Hide by Demo Inn
</div>

<img src="https://github.com/LittleSound.png" rounded-full w-40 abs-tr mt-16 mr-12/>

<div flex="~ gap2">

</div>

<!--

Let me introduce myself first.

My name is Rizumu, and my GitHub handle is LittleSound.

I'm an indie developer from China, and I’m really passionate about open source.

I’m part of the Vue Vapor team, for over the past year, I’ve been deeply involved in building this exciting new features for Vue.

And, besides working on Vue,
I’ve also created some fun projects like nolebase, Qrs, Guii AI, and Interline Translate. I'm also part of the Elk team.

Alright, so let's get started!
-->

---
class: text-center
---

<div fixed inset-0 flex="~ col items-center justify-center gap10">
  <div i-logos-vue text-50 />
  <h2>Started in 2013</h2>
</div>

<!--
You can see, 10 years ago, Vue.js came onto the scene and built an amazing community.

Vue is a front-end framework with 2 million weekly active users.
-->

---
class: text-center
---

<div fixed inset-0 flex="~ col items-center justify-center gap10">
  <div i-logos-vitejs text-50 />
  <h2>Started by Vue</h2>
</div>

<!--
From that, we also got Vite - a very popular front-end build tool.

Today, I want to tell you about the next upgrade in Vue - [click] it's called Vapor!!
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
If you are a big fan of Vapor, you might already know what I'm going to introduce:

[click] Vapor is Vue without the Virtual DOM, like Solid, right??

Yes. but instead of getting into this too much, let's think about this in another way.

[click] If you were Evan You, the creator of Vue, how would you make Vue even faster?
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
    <PerformanceProgress v-click="4" name="Vanilla JS" :progress="100" highlight icon="i-logos:javascript" />
    <PerformanceProgress v-click="3" name="Vue vDOM" :progress="80.6" icon="i-logos:vue" />
    <PerformanceProgress v-click="2" name="React" secondary="Jotai" :progress="68" icon="i-logos:react" />
  </div>
</v-click>

<!--
Well, [click] If you look at the current performance rankings of front-end frameworks:

First, you'll notice that, [click] React performance score is 68.

Now, what ideas would you think. how would you go about making Vue even faster? Continue using Virtual DOM | and then do more optimization? If you have seen some of Evan's talks, you might know that, [停顿] yes! Vue | has already
 | added a lot of | optimizations  | to the Virtual DOM.

[click] So now Vue is here, and it scored | eighty (80).

If you still want to get faster, what will you do? How will you solve this?

You may want to know who is the best one on the performance list? It solved this. but how did it?

[click] That one is Vanilla JS. It is the golden standard of this benchmark, which is 100 (a hundred) out of 100.

What is vanilla? It is the default flavor of the ice cream we eat.

So Vanilla is the native DOM operation code, yes. It directly operates on the DOM itself, without Virtual DOM.
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
Why is it so fast? It's because it's highly flexible. If the person | who writes it masters enough optimization techniques, they can do a lot of "hacker tricks" based on this test to make the performance even better.

Let's take a look a example.

[click] For example, "reduced updates".

[click] First, let's look at a bad approach. The bad approach is this ...

you got an element. and if you want to change the width and height, and you have several values.

Then you might write it this way, changing one value at a time.

because it will re-render every time, this would be very slow.

[click] A better approach is that you can first merge all the updates and then apply them | all at once.

[click] Here's another example, "event delegation".

[click] for example. The bad approach is that I have a list with 10,000 rows. And each item has a delete operation. So I'll have 10,000 events attached. This will be very slow too.

[click] The better approach is that | we could have one listener over the parent, and then look for the element we want to handle. This way we have only one event listener, so it will be faster as well.

[click] There are many other optimization techniques

TODO: 增加更好的例子，可以查询相关的文章找一下
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
    Advance<br>
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
There are many | other optimization techniques, such as | template reuse, reactive programming, and so on, which can also speed it up.

So we actually don't need Virtual DOM, right?

But sometimes using native DOM APIs directly is hard - you need to learn many tricks.

And you'll also need to think about how to work together with your team.

That's when we use frameworks.

But how do we solve this problem?

The answer is | right here, [click] the answer is | in Vite.

We haven't been directly writing DOM APIs for a long time, and we also don't write actual running JS directly, do we?

We actually all install Vite to help us.

[click] Because behind Vite, we know there's something called Compiler.
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
It can take the source code, [click] like Vue SFC file, and [click] based on the rules | you set up, [click] compile it into runtime code.
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
Actually, we have been using this way to compile [click] Virtual DOM runtime in Vue for a long time.

But like I said before, Virtual DOM runtime is too far from real DOM operations.

It is not easy to change, and in every re-render, extra work runs every time, whether you need them or not.

So we want to use Compiler, but take away Virtual DOM, and use Compiler to [click] build DOM operations right away.
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
So, back to Vapor. if we make a smart enough compiler.

[click]  It can take a Vue SFC file, [click] and compile it into native DOM operations.

And it knows how to use these "hacker tricks" to optimize performance.

So our framework can achieve performance close to Vanilla in benchmark tests.

This is the foundation of Vapor's all.
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

<div size-full flex="~ col items-center justify-center" font-500>
  <h1
    class="!text-15"
  >🍳 The status of Vapor</h1>
</div>

<!--
Let's look at what this way makes for Vue Vapor.
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
First of all,

[click] Vapor is a subset of Vue.

So... you just need to [click]  switch the vapor flag on.

you can get fast speed without learning a new framework or hard tricks to use it.
-->

---
class: text-center
clicks: 2
---

<h1>Performance of Vapor</h1>

<div mt10 px10 flex flex-col gap2 relative>
  <TransitionGroup tag="div" name="list" class="relative flex flex-col gap2">
    <div v-click="2" font-hand abs-tr top="-14" rotate-13 text-2xl>Longer is better!</div>
    <PerformanceProgress v-click name="Vanilla JS" :progress="100" icon="i-logos:javascript" />
    <div v-if="$clicks > 1">
      <PerformanceProgress name="Vue Vapor" :progress="90" icon="i-logos:vue" highlight />
    </div>
    <PerformanceProgress v-click="1" name="Vue vDOM" :progress="80.6" icon="i-logos:vue" />
    <PerformanceProgress  v-click="1" name="React" secondary="Jotai" :progress="68" icon="i-logos:react" />
  </TransitionGroup>

  <p mt10="!" text-xs op60 v-click="2">
  * <a href="https://x.com/sanxiaozhizi/status/1842807976157155432/photo/1" target="_blank">The results</a> are based on <a href="https://github.com/krausest/js-framework-benchmark" target="_blank">js-framework-benchmark</a>, and tested on a MacBook Pro M1 Max.
  </p>

</div>

<!--
So how fast is Vapor?

[click] If we say VanillaJS performance score is 💯 one hundred,

[click] then Vapor's score now is ninety (90).

that's faster than the Virtual DOM
-->

---

<h1>Architecture</h1>

<Architecture />

<!--
And thanks to Vapor Compiler's IR architecture. [click] Besides `template` syntax, [click] we also can compile from JSX to Vapor runtime.

Big thanks to Gao Fei (zhiyuanzmj) for adding the JSX feature!
-->

---
class: text-center
---

<h1>Bundle size</h1>

<div v-click mt30>
  <template v-if="$clicks === 1">
    <AnimateNumber v-slot="{ number, target }" :value="53.3" :duration="500">
      <div
        text-7xl font-mono font-bold
        text-transparent bg-clip-text bg-gradient-to-tl from-green-400 via-teal-400 to-blue-500
        :style="{ transform: `scale(${1 + (number / target / 4)})` }"
      >
          {{ number.toFixed(1).padStart(4, '0') }}%
      </div>
    </AnimateNumber>
    <div op80 mt-7 text-2xl flex gap1 items-center justify-center>
      <div scale-120 i-ri:arrow-down-double-line animate-pulse animate-duration-1000  />
      Reduced compared to vDOM mode
    </div>
    <div mt30 text-sm op60>* Comparison of Vapor and vDOM runtime only</div>
  </template>
</div>

<!--
and because there is no Virtual DOM, Vapor's runtime size is smaller.

Right now, compared to Virtual DOM mode, [click] the runtime size is fifty-three percent smaller. (53.3%)
-->

---

### Recap

- Vapor is a subset of Vue, they can work together
- Vapor will keep improving performance and bundle size
- Vapor will have better JSX support
- Uses IR architecture
- Supports DevTools (thanks to contributors)
- Fine-grained rendering based on reactivity

<!--
We covered a lot just now.

so Vapor is Vue's new upgrade.

It's a subset of Vue, and they can work together.

Vapor makes things faster and bundle size smaller.

It will have better JSX support. and Vapor has many more plans for the future.

TODO: 可以参考 Apple 的那个发布会的那个总结图片，就是一个 bento 样式的页面，而且我们可以用总结来写一些来不及讲的细节问题
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
All these features wouldn't be possible without [click] every contributor in the Vue community.

I want to thanks for their work.
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
I remember when I first contributed with Vapor. One day I saw Kevin on Twitter saying: "Who wants to help write Vue Vapor? If you come find me, I can teach you how to do it."

At that time. I didn't know what Vapor was, but I was really into Vue.

So... I bought a train ticket for the next day.

After I came back, I looked at Vapor's code all night.

but couldn't understand it. I cried, feeling like I couldn't get it at all.

But the next day | I looked many more times, and finally understood.

Now, I've written lots of code for Vapor.

So... when first joining open source, stepping out of what felt safe, [click] interest is really the best teacher and gives you lots of energy.

Later I also sent PRs to Vue Core.

That PR took about a year to be accepted. The same kind of PR in Vue Vapor would take just a day or two.

The people who keep the project running need to check each PR very carefully to avoid breaking things, and these big projects often have many PRs waiting, with only 2-3 main people checking them.

[click] So it makes sense why we wait so long ｜ when contribute these projects.

Instead, contribute new projects like Vapor that you like and that are growing fast is a better choice.

[click] They accept PRs faster, often change their code, and have more chances to contribute.

For example, things that aren't done yet or problems that need fixing - many of these are easy to find and fix.
-->

---
class: text-center
---

<h1 fixed top-10 left-10 op80>My way to Open Source</h1>

<div size-full flex="~ col items-center justify-center gap10">
  <h1 class="!text-15">Where to start contribute?</h1>
</div>

<!--
Really, even then...

even after I read Vue Vapor's code all night, when I went to find Kevin, I had no idea what I could do, and Kevin had to think for a long time too. Back then, I knew almost nothing about Vapor.
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
That day Kevin told me a lot, but it was hard to understand all the complex stuff in such a short time. The single thing I remember is: [click] I could help write unit tests.

because if I couldn't fix the broken tests. I could mark the tests as TODO or fail in the PR. This way, others in the community would know there was a todo test here.

While reading old unit tests and trying to write new ones, I learned how the project worked at a deeper level.

Then, the next day after I went back. I found a broken test that was very simple, and I thought I knew how to fix it. I decided to submit a fix PR [click].

This is the good thing about writing unit tests. You quickly find some test cases that you think you know how to fix.

Don't worry about making mistakes. This was our next step: fix somethings.

If you keep doing it, you'll get better at this process.

And by this time, other project contributors will know who you are. If they want to add a simple new feature, you can confidently say:

[click] "I want to try building this." Again: "Don't worry about mistakes or failing." At this point, you're starting to help build a new feature.

As you understand the project better and become known by other developers for your help, you'll do more than just write code.

[click] You'll also share your ideas, and other active helpers will build them. By this time, you've become an important part of this project.

Doing all these things takes a lot of time, and even more as you get deeper into the community.

[click] Based on how much time you have and what feels comfortable to you, you can stop anywhere along this path and enjoy that level of open source work.
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
That's my Vapor open source story.

[click] I hope to see your story here too.

【适当停顿】

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
So... today, [click] we invented Vapor together. [click] Then we talked about its performance, its architecture, its roadmap, [click] and thanked the contributors, and got my open source story.

That's all for this talk. [click] I practiced this session many times...

TODO: 随点击顺序出现
TODO: 更好的总结配图
-->

---

# References

- Vue Vapor
  - [Vue Vapor](https://github.com/vuejs/vue-vapor)
  - [Slides: Vue Vapor: Reinvention](https://github.com/sxzz/talks/tree/main/2024-10-vue-fes-japan)
  - [Slides: Yak Shaving](https://talks.antfu.me/2024/vue-fes-japan/)
  - [Thinking Granular: How is SolidJS so Performant?](https://dev.to/ryansolid/thinking-granular-how-is-solidjs-so-performant-4g37)

- English and Talks
  - [iPhone 1 launch event speech](https://www.google.com/search?q=iPhone+1+launch+event+speech&sourceid=chrome&ie=UTF-8)
  - [English Learning: the Refold Roadmap](https://refold.la/roadmap/)

<div h-10 />

**Thank you, [Kevin Deng](https://github.com/sxzz) and [Anthony Fu](https://github.com/antfu).**

<!--
I practiced this session many times.

So... I hope you liked it, and I hope you found something from it.
-->

---
layout: center
class: 'text-center pb-5'
---

# Thanks！

<div op75>

**Slides can be found at [github.com/LittleSound/talks](https://github.com/LittleSound/talks)**

Slides build with [Slidev](https://sli.dev)

</div>

<!--
and Thank you for joining us.
-->

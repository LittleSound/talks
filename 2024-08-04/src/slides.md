---
layout: intro
theme: seriph
background: /demo.png
transition: fade
---

# Rizumu｜绚香音

<div class="[&>*]:important-leading-10 opacity-80">

{Vue} {Elk} 团队成员<br>
{Nolebase} {InterlineTranslate} {SlimeForm} {xUse} 作者<br>
自由职业，正在创造 {Guii.AI}<br>

</div>

<div my-10 w-min flex="~ gap-1" items-center justify-center>
  <div i-ri-github-line op50 ma text-xl ml4/>
  <div><a href="https://github.com/LittleSound" target="_blank" class="border-none! font-300">LittleSound</a></div>
  <div i-ri-twitter-x-line op50 ma text-xl ml4/>
  <div><a href="https://x.com/OikawaRizumu" target="_blank" class="border-none! font-300">OikawaRizumu</a></div>
</div>

<img src="https://github.com/LittleSound.png" rounded-full w-40 abs-tr mt-16 mr-12/>

<div flex="~ gap2">

</div>

<!--
大家好。

我是小音，也叫 Rizumu 或 LittleSound。

我是一名热爱开源的独立开发者，同时也是 Vue Team 的成员。Vue 是当前拥有 200 万周活跃用户的前端框架。
-->

---
layout: intro
background: /demo.png
transition: fade
---

<img class="absolute inset-0 w-full h-full object-cover" src="/demo.png" />

---
theme: seriph
layout: cover
background: /demo.png
transition: slide-left
---

<div space-y-10 flex flex-col items-center>
  <div flex justify-center>
    <img src="/logo-guii.png" class="size-40" alt="Guii" />
  </div>
  <div p-5 bg="white/80" backdrop-blur-sm shadow-xl rounded-2xl text-black>
    <p class="!p-0 !m-0" text-left text-gray-7>
      > console.log('hello, Guii.AI DevTools')
    </p>
    <h1 class="!p-0 !m-0">
      Hello,
      <span class="font-900 bg-clip-text text-white/0 bg-gradient-to-rb from-green-400 to-blue-500">
        Guii.AI
      </span>
      DevTools
    </h1>
  </div>
</div>

<!--
通过这次机会，我想向大家介绍一下我正在开发的项目：Guii.AI DevTools
 -->

---
layout: cover
transition: fade-out
---

<h1>
  什么是
  <span class="font-900 bg-clip-text text-white/0 bg-gradient-to-rb from-green-400 to-blue-500">
    Guii.AI
  </span>
  DevTools?
</h1>

---

# Guii.AI 的产品定位

<v-clicks>

- 前端开发者
- 独立开发者
- 初创小团队

</v-clicks>

---

他们的的现状

# 程序员在编写代码时越来越多地使用 AI

<div my-7 grid grid-cols-2 gap-4>
  <Product
    name="GitHub Copilot"
    intro="GitHub推出的AI编程工具"
    src="/github-copilot.png"
  />

  <Product
    name="Fig"
    intro="AI 终端命令自动补全"
    src="/fig.png"
  />

  还有很多...
</div>

<v-click>

# 前端的 AI 工具

效果并不理想

<div mt-7 grid grid-cols-2 gap-4>
  <Product
    name="v0.dev"
    intro="Al 生成前端 React UI 组件，由 Vercel 推出"
    src="/v0-dev.png"
  />

  <Product
    name="ancodeai"
    intro="UI 组件生成"
    src="/ancodeai.png"
  />
</div>

</v-click>

<!--

1. 程序员在编写代码时越来越多地使用 AI，但在 Web 前端开发中，常规的 AI Copilot 工具效果并不理想。

2. click

3. 尽管市场上已有一些针对前端的 AI 工具，但它们存在各种问题。比如 v0.dev 在它的网站平台上提供代码生成服务，尽管很多人在使用，但是生成的代码一旦交付到用户的项目中，就无法在由 v0 平台上进行二次修改了。

-->

---

# Nuxt DevTools

<img src="/nuxt-devtools.jpg" />

<!--

前端开发工具本身也在发展中。

比如 Vuejs 生态有类似 Nuxt DevTools 这样的产品，它探索了前端开发者体验的新方向，直接在开发者正在开发中的项目上依据项目技术栈和已有代码上下文提供开发者工具。

但是它并没有融入生成式 AI Copilot 的能力。

-->

---
layout: cover
---

😣 问题是什么？

<v-click>

# ⏰ 写前端真的很花时间！

</v-click>

<!--

在我们了解了这些信息之后，Guii 尝试解决的问题是什么？

-->

---
layout: cover
---

<p text-gray-3>
Guii AI DevTools 旨在提高您的生产力
</p>

<h1 v-click>
  写代码效率
  <span class="font-900 bg-clip-text text-white/0 bg-gradient-to-rb from-green-400 to-blue-500">
  ×10
  </span>
</h1>

<!--

我正在开发的 Guii.AI 通过直接在项目中提供 AI 前端开发者工具的形式，并结合 AI 对项目技术栈和已有代码的感知，提供针对前端场景优化的工具，更智能、更深入地帮助开发者编写代码。这与市面上现有的前端 AI 工具有很大不同。

-->

---

<SlidevVideo autoplay class="absolute inset-0" controls w="100%" h="100%">
  <source src="https://pub-02c0d9cf56bf494ca028e591af37bfb5.r2.dev/Guii-ai-devtools-demo.mp4" />
</SlidevVideo>

---
layout: cover
---

# Guii.AI 的诞生

---

# Neko: 感觉生成式 UI 很有意思

- Apple Intelligence
- Devv.AI

<v-click>

# Rizumu: 来做一个生成前端代码的平台吧

</v-click>

---

过去的 Guii.AI

<v-click>

# Web Guii.AI

在网站上生成代码

</v-click>

<v-click>

<img src="/guii-web.jpeg" w-full h-340px object-contain />

</v-click>

---

和现在有什么不同？

# DevTools

<v-clicks>

- 🙌 触手可及 - 直接安装在开发环境中无需打开单独的网站
- 🫧 项目上下文 - 感知项目上下文，生成的代码更贴合项目
- ✍️ 直接写入文件 - 生成代码直接改到对应文件中，无需复制粘贴
- 🆕 不止局限于生成新页面 - 项目开发任何阶段随时生成

</v-clicks>

---

Guii.AI

# DevTools 背后的架构

<v-clicks>

- Compiler 编译器 - 注入 source map 源码映射，实现元素查找能力
- Client - 注入 UI 到开发页面
- Server - 与 Client 通信，生成代码
- File System 文件系统 - 调取选中的源码，写入生成后的文件

</v-clicks>

---

我们想
# 做的更多

<v-clicks>

- 🏗️ 框架无关 - 支持多种框架，Vue、React、Angular、Svelte...
- 📦 打包器无关 - 支持多种打包器，Webpack、Vite、Rollup...
- 🖼️ 组件库无关 - 支持多种组件库，Shadcn、Element...
- 🚀 更多深入前端开发的提效功能

</v-clicks>

---
layout: cover
---

# 谢谢！

幻灯片可在 [GitHub.com/LittleSound/talks](https://github.com/LittleSound/talks) 查看

<div mt-10 flex flex-col justify-center items-center gap-5 text-left>
  <div flex items-center gap-4>
    <img src="/logo-guii.png" class="size-30" alt="Guii" />
    <div space-y-3>
      <h3 class="!text-xl"><span rounded-xl bg-blue-3 text-black p-1 px-4>与 Guii 一起写前端</span></h3>
      <h1 text-white class="!text-white">加群了解更多信息！</h1>
    </div>
  </div>
  <div flex flex-col justify-start items-center h-screen>
    <div bg-white rounded-t-2xl h-400px>
      <img h-230px object-cover src="/qrc.png" />
    </div>
  </div>
</div>

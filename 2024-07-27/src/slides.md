---
theme: seriph
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

# Guii.AI 是给谁用的?

产品定位

<v-clicks>

- 前端开发者
- 独立开发者
- 初创小团队

</v-clicks>

---
layout: cover
---

😣 痛点是什么？

<v-click>

# ⏰ 写前端真的很花时间！

</v-click>

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

<div flex flex-col justify-center items-center gap-5>
  <div flex items-center gap-4>
    <img src="/logo-guii.png" class="size-25" alt="Guii" />
    <div space-y-3>
      <h3 class="!text-xl"><span bg-blue-3 text-black p-1 px-2>与 Guii 一起写前端</span></h3>
      <h1 text-white class="!text-white">加群了解更多信息！</h1>
    </div>
  </div>
  <div flex justify-center items-center>
    <div bg-white rounded-t-2xl>
      <img h-400px object-cover src="/qrc.png" />
    </div>
  </div>
</div>

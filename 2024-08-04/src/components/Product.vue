<script setup>
defineProps({
  name: {
    type: String,
    required: true,
  },
  intro: {
    type: String,
    required: true,
  },
  src: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <div flex gap-4 bg="emerald/20" p-4 rounded-3xl border="emerald/50 1">
    <img :src="src" size-14 of-hidden rounded-xl>
    <div flex flex-col gap-1>
      <h3 class="!p-0 !m-0 !text-xl">
        {{ name }}
      </h3>
      <p class="!p-0 !m-0 !text-base">
        {{ intro }}
      </p>
    </div>
  </div>
</template>

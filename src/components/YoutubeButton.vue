<template>
  <a :href="href" target="_blank" class="border-2 border-red-600 font-semibold text-red-600 px-2 py-1 rounded hover:bg-red-600 hover:text-white transition-colors">
    <slot></slot>
  </a>
</template>

<script setup>
  const props = defineProps({
    href: String
  })
</script>
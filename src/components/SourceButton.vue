<template>
  
    <a :href="href" target="_blank" class="border-2 border-green-600 font-semibold text-green-600 px-2 py-1 rounded hover:bg-green-600 hover:text-white transition-colors">
      <slot>view</slot>
    </a> 
  
</template>

<script setup>
  const props = defineProps({
    href: String
  })
</script>
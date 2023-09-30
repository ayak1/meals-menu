<template>
  <!-- <pre>{{ingredients}}</pre> -->
  <div class="p-8">
    <h1 class="font-bold text-4xl mb-3">Ingredients</h1>
    <input type="text" 
           v-model="keyword" 
           class="rounded border-2 border-gray w-full mb-3" 
           placeholder="search for ingredients"
    >
    <router-link :to="{name:'byIngredient',params: {ingredient: ingredient.strIngredient} }" v-for="ingredient of computedIngredients" :key="ingredient.idIngredient" class="block bg-white p-3 mb-3 rounded shadow">
      <h3 class="text-2xl font-bold">{{ingredient.strIngredient}}</h3>
      <p class="font-semibold">{{ingredient.strDescription}}</p>
    </router-link>
  </div>
</template>
<script setup>
import {onMounted , ref} from 'vue';
import {computed} from '@vue/reactivity'
import axiosClient from '../axiosClient';

const keyword = ref('');
const ingredients = ref([]);
const computedIngredients = computed(() => {
  if(!computedIngredients) return ingredients
  return ingredients.value.filter((i) =>  {
    return (i.strDescription || '').toLowerCase().includes(keyword.value.toLowerCase()) ||
    i.strIngredient.toLowerCase().includes(keyword.value.toLowerCase())
  });
});
onMounted(() => {
  axiosClient.get(`list.php?i=list`)
  .then(({data}) => {
    ingredients.value = data.meals
  })
})
</script>
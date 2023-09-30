<template>
  <div  class="bg-white shadow rounded-lg">
    <router-link :to="{name:'mealDetails',params:{id: meal.idMeal}}">
      <img class="rounded-t-xl w-full h-56 object-cover" :src="meal.strMealThumb" :alt="meal.strMeal">
    </router-link>
    <div class="p-3">
      <h3 class="font-bold">{{meal.strMeal}}</h3>
      <p class="px-2">Lorem ipsum, dolor sit amet consectetur adipisicing elit. Praesentium eos perferendis porro. Impedit, sit ipsa? Voluptatibus quo saepe rem nulla!</p>
      <div class="py-3 flex gap-3">
        <YoutubeButton :href="meal.strYoutube">Youtube</YoutubeButton>
        <SourceButton :href="meal.strYoutube">View</SourceButton>   
      </div>
    </div>
  </div>
</template>

<script setup>
import YoutubeButton from '../components/YoutubeButton.vue';
import SourceButton from '../components/SourceButton.vue';
  
  // ^===> const props = defineProps({
  //   meal: {}
  // })
  const {meal} = defineProps({
    required: true,
    meal: Object
  })
</script>
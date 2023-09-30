<template>
  <div class="max-w-[800px] mx-auto mt-7">
    <!-- <pre>{{meal}}</pre> -->
    <h1 class="text-5xl font-bold mb-5">{{meal.strMeal}}</h1>
    <img :src="meal.strMealThumb" :alt="meal.strMeal" class="max-w-[800px] w-full">
    <div class="grid grid-cols-1 sm:grid-cols-3 text-lg py-2">
      <p><strong class="font-bold">Category:</strong> {{meal.strCategory}}</p>
      <p><strong class="font-bold">Area:</strong> {{meal.strArea}}</p>
      <p><strong class="font-bold">Tags:</strong> {{meal.strTags}}</p>
    </div>
    <div class="my-3 max-w-[800px]">
      {{ meal.strInstructions }}
    </div>
    <div class="grid grid-cols-1 sm:grid-cols-2">
      <div>
        <h2 class="text-2xl font-semibold mb-2">Ingredients</h2>
        <ul>
          <template v-for="(el,index) of new Array(20)">
            <li v-if="meal[`strIngredient${index+1}`]">
              {{index+1}}. {{ meal[`strIngredient${index+1}`] }}
            </li>
          </template>
        </ul>
      </div>
      <div>
        <h2 class="text-2xl font-semibold mb-2">Measures</h2>
        <ul>
          <template v-for="(el,index) of new Array(20)">
            <li v-if="meal[`strMeasure${index+1}`]">
              {{index+1}}. {{ meal[`strMeasure${index+1}`] }}
            </li>
          </template>
        </ul>
      </div>
    </div>
    <div class="mt-4 py-3 flex gap-3">
      <YoutubeButton :href="meal.strYoutube">Go To YouTube</YoutubeButton>
      <SourceButton :href="meal.strYoutube">View Original Source</SourceButton>   
    </div>
  </div>
</template>

<script setup>
import {onMounted,ref} from 'vue'
import { useRoute } from 'vue-router'
import axiosClient from '../axiosClient';
import YoutubeButton from '../components/YoutubeButton.vue';
import SourceButton from '../components/SourceButton.vue';

const route = useRoute();
const meal = ref({})

onMounted(()=>{
  axiosClient.get(`lookup.php?i=${route.params.id}`)
  .then(({data})=>{
    debugger;
    meal.value = data.meals[0]
  })
})
</script>
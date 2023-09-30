<template>
  <div>
    <div class="flex justify-center gap-5 md:gap-4 sm:gap-3 mt-3 flex-wrap">
      <router-link :to="{name: 'byLetter' , params:{letter}}" v-for="letter in letters" :key="letter" class="text-yellow-500 mx-3 text-sm lg:text-lg md:text-xl font-bold mt-3 drop-shadow-md">
        {{ letter }}
      </router-link>
    </div>
    <Meals :meals="meals"/>
  </div>
</template>

<script setup>
import {computed} from '@vue/reactivity';
import {onMounted, watch} from 'vue';
import { useRoute } from 'vue-router';
import Meals from '../components/Meals.vue';
import store from '../store';

const route = useRoute();
const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("");
const meals = computed(()=> store.state.mealsByLetter)

watch(route, () => {
  store.dispatch('searchMealsByLetter', route.params.letter)
})
onMounted(() => {
  store.dispatch('searchMealsByLetter',route.params.letter)
})
</script>
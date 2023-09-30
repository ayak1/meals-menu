<template>
  <Meals :meals="meals"/>
</template>

<script setup>
import {computed} from '@vue/reactivity';
import {onMounted} from 'vue';
import { useRoute } from 'vue-router';
import Meals from '../components/Meals.vue';
import store from '../store';

const route = useRoute();
const meals = computed(()=> store.state.mealsByIngredient)

onMounted(() => {
  // debugger;
  store.dispatch('searchMealsByIngredient',route.params.ingredient)
})
</script>
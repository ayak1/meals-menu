<template>
  <div class="grid grid-cols-1 md:grid-cols-3 gap-10 p-8">
    <MealItem v-for="meal in meals" :key="meal.idMeal" :meal="meal"/>
  </div>
  <div v-if="!meals.length" class="text-gray-600 text-lg flex justify-center underline ">There are no meal</div>

</template>

<script setup>
import MealItem from '../components/MealItem.vue';
const props = defineProps({
  meals: {
    required: true,
    type: Object
  }
})
</script>
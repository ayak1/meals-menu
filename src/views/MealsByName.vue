<template>
  <div class="p-8">
    <input type="text" 
           v-model="keyword" 
           class="rounded border-2 border-yellow-500 placeholder:text-yellow-500 shadow w-full" 
           placeholder="search for meals"
           @change="searchMeals"
           >
  </div>
  <Meals :meals="meals" />
</template>

<script setup>
  import { computed } from '@vue/reactivity'
  import {onMounted, ref } from 'vue'
  import {useRoute} from "vue-router"
  import store from '../store';
  import Meals from '../components/Meals.vue';

  const route = useRoute();
  const keyword = ref('');
  const meals = computed(()=> store.state.searchedMeals)
  function searchMeals() {
    if(keyword.value){
      store.dispatch('searchMeals',keyword.value)
    }else{
      store.commit('setSearchedMeals',[])
    }
  }
  onMounted(() => {
    keyword.value = route.params.name
    if(keyword.value){searchMeals()}
  })
</script>
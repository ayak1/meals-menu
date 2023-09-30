<template>
  <header class="bg-yellow-500 text-white font-semibold text-xs lg:text-lg md:text-xl  shadow-md h-14 flex justify-between ">
    <router-link class="inline-flex items-center px-5" :to="{name:'home'}">Home</router-link>
    <div class="flex items-center gap-2">
      <router-link :to="{name: 'byName'}" class="inline-flex items-center px-5 h-full transition-colors hover:bg-white hover:text-yellow-500 " >Search Meals</router-link>
      <router-link :to="{name: 'byLetter'}" class="inline-flex items-center px-5 h-full transition-colors hover:bg-white hover:text-yellow-500 " >Meals By Letter</router-link>
      <router-link :to="{name: 'ingredients'}" class="inline-flex items-center px-5 h-full transition-colors hover:bg-white hover:text-yellow-500 " >Meals By Ingredients</router-link>
    </div>
  </header>
</template>
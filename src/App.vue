<script setup lang="ts">
import Title from './components/Title.vue'
import SelectIngredients from './components/SelectIngredients.vue'

let name: string = 'Jean-Baptiste'

</script>

<template>
  <header>

    <Title :name="name" msg="Welcome in my webapp, RecipeFinder"/>  

  </header>


  <main>

    <SelectIngredients />
    
  </main>
</template>

<style>
@import './assets/base.css';

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

header {
  line-height: 1.5;
  text-align: center;
}

</style>

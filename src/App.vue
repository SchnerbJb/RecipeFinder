<script setup lang="ts">
import Title from './components/Title.vue'
import SelectIngredients from './components/SelectIngredients.vue'

let name: string = 'Jean-Baptiste'

let ingredients: { id: Number, text: String, amount: String, unit: String }[] = []

</script>

<template>
  <header>

    <Title :name="name" msg="Yo a toi"/>  

  </header>


  <main>

    <SelectIngredients @response="(ingredientsList) => ingredients = ingredientsList" />
    
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

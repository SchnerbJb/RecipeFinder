<script lang="ts">

import { defineComponent } from "vue";
import { useFetch } from '../services/fetchAPI'
import SearchRecipe from './SearchRecipe.vue'

let id: number = 1

export default defineComponent({
    data() {
        return {
            text: "",
            amount: "",
            unit: "",
            ingredients: new Array<{
                id: Number;
                text: String;
                amount: String;
                unit: String;
            }>(),
            response: new Object
        };
    },
    methods: {
        addList() {
            if (this.text === "" || this.amount === "" || this.unit === "") {
                return;
            }
            this.ingredients.push({ id: id++, text: this.text, amount: this.amount, unit: this.unit });
            this.text = "";
            this.amount = "";
        },
        searchRecipe() {
            console.warn("searching...");
            this.response = useFetch("https://api.spoonacular.com/recipes/complexSearch?apiKey=" + import.meta.env.VITE_API_KEY);
            console.log(this.response);
        }
    },
    components: { SearchRecipe }
})

</script>

<template>

    <h2 class="p-3 m-3">What ingredients do you have ?</h2>
    

    <div class="container border p-3 rounded">
        <form @submit.prevent="">
            <div class="form-group row">
                <label for="name" class="col-sm-1 col-form-label ml-2"><span>Name</span></label>
                <input v-model="text" type="text" id="name">
            
            </div>
            <div class="form-group row">
                <label for="amount" class="col-sm-1 col-form-label ml-2">Quantity</label>
                <input v-model="amount" type="text" id="amount">
            
                <div class="col-md-4 row ml-2">
                    <select v-model="unit" name="unit">
                        <option value="L">L</option>
                        <option value="Kg">Kg</option>
                        <option value=" ">Unity</option>
                    </select>
                </div>
            </div>
            <div><button class="btn btn-success mt-2" @click="addList">Add Ingredient</button></div>
        </form>
    </div>

    <div class="container border p-3 mt-3 rounded">
        <h3>List of ingredients :</h3>
        <div v-if="ingredients.length !== 0">
            <ul>
                <li v-for="ingredient in ingredients">
                    {{ ingredient.id }} : {{ ingredient.amount }} {{ ingredient.unit }} {{ ingredient.text }}
                </li>
            </ul>
        </div>
        <div v-else>
            <p>Nothing yet</p>
        </div>

        <SearchRecipe />

        <!-- <div>
            <button class="btn btn-success mt-2" @click="searchRecipe">Search Recipes</button>
        </div> -->
    </div>

    <div class="container border p-3 mt-3 rounded">
        <h3>Response API</h3>
        <div v-if="Object.keys(response).length !== 0">
            <div v-for="data in response['data']['results']">
                <div><img class="img-responsive w-25 h-25" :src='data["image"]' > {{ data["title"] }}</div>
            </div>
        </div>
    </div>

</template>

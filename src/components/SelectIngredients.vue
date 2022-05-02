<script lang="ts">

let id: number = 1

import { defineComponent } from "vue";

export default defineComponent({
    data() {
        return {
            text: '',
            amount: '',
            unit: '',
            ingredients: new Array<{ id: Number, text: String, amount: String, unit: String }>()
        }
    },
    methods: {
        addList() {
            this.ingredients.push({ id:id++, text: this.text, amount: this.amount, unit: this.unit })
            this.text = ''
            this.amount = ''
        }
    }
})

</script>

<template>

    <h2>What ingredients do you have ?</h2>
    

    <div class="container border p-3">
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
            <div><input type="submit" class="btn btn-success mt-2" value="Search Recipes" /></div>
        </form>
    </div>

    <div class="container border p-3 mt-3">
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

    </div>

</template>

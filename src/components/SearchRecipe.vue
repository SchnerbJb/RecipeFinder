
<script lang="ts">

import { defineComponent } from 'vue'

export default defineComponent({

    methods: {
        search() {
            alert('Searching : ')
        }
    }
})

</script>

<template>
    <div>
        <button class="btn btn-success mt-2" @click="search">Search Recipes</button>
    </div>
</template>

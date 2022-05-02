<script lang="ts">

import { defineComponent } from 'vue';

export default defineComponent({
    props: {
        name: String,
        msg : { type: String }
    }
})

</script>

<template>

    <div class="mb-14">
        <h1>Salut, {{ name }} </h1>
        <h4>{{ msg }}</h4>
    </div>

</template>
<script setup>
import { onMounted, defineProps, inject, watch } from 'vue';

// const { route } = defineProps({
//     'route': 'string'
// });
const route = inject('route');

const changeRoute = defineEmits(['changeRoute'])

watch(route, (route) => {
    console.log(route, 'd')
})


</script>

<template>
    <main class="container">
        <div class="main__content">
            <!-- <h1>{{ route }} e</h1> -->

            <img class="main__img-medails" src="/frame.png" alt="frame">
            <button @click="() => { route = 'countries' }" class="btn"><img src="/ico-countries.svg" alt="Countries">Countries</button>
            <button @click="() => { route = 'disciplines' }" class="btn"><img src="/ico-disciplines.svg" alt="disciplines">Disciplines</button>
        </div>
    </main>
</template>
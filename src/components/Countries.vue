<script setup>
import { onMounted, defineProps, inject, provide, watch, ref } from 'vue';

// const { route } = defineProps({
//     'route': 'string'
// });
const route = inject('route');


// onMounted(() => {
// })

// watch(route, (route) => {
//     console.log(route, 'd')
// })

const countries = inject('countries')


const country = inject('country');
const countrySetup = (countryNewValue) => {
    console.log(countryNewValue)
    country.value = countryNewValue;
    route.value = 'country'
}

</script>

<template>
    <main class="container">
        <div class="main__content">
            <!-- <h1>{{ route }} e</h1> -->

            <!-- <img class="main__img-medails" src="/frame.png" alt="frame"> -->
            <h1 class="header__text">Countries</h1>
            <div v-for="country in countries">
                <button @click="() => countrySetup(country)" class="btn"><img width="40" :src=country.flag :alt="country.name">{{country.name}}</button>
                <!-- <button class="btn"><img src="/ico-disciplines.svg" alt="">Discipliness</button> -->
            </div>
        </div>
    </main>
</template>
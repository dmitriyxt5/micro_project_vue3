<script setup>
import { onMounted, defineProps, inject, provide, watch, ref } from 'vue';

const country = inject('country');
const route = inject('route');
const medalsIt = inject('medalsIt');


// provide('country', countries)
onMounted(() => {
    console.log(country.value.medals, 'country')
})

const countMedals = ref(country.value.medals.gold + country.value.medals.silver + country.value.medals.bronze);

const medalsSetup = (medal) => {
    console.log('medal=', medal);
    route.value = 'medals';
    medalsIt.value = {
        'medal': medal,
        'count': countMedals,
    };
    console.log('medal=', medal)
}

</script>

<template>
    <main>
        <div class="main__content main--country container">
            <!-- <h1>{{ country }} e</h1> -->

            <!-- <img class="main__img-medails" src="/frame.png" alt="frame"> -->
            <h1 class="header__text">{{ country.name }}</h1>
            <img width="125" :src="country.flag" alt="">
            <div v-for="country in countries">
                <button @click="() => countrySetup(country)" class="btn"><img width="40" :src=country.flag :alt="country.name">{{country.name}}</button>
                <!-- <button class="btn"><img src="/ico-disciplines.svg" alt="">Discipliness</button> -->
            </div>

        </div>
        
        <table class="country__table">
                <tr>
                    <th>GOLD</th>
                    <th>SILVER</th>
                    <th>BRONZE</th>
                    <th>TOTAL</th>
                </tr>
                <tr>
                    <td v-for="count in country.medals">{{ count }}</td>
                    <td>{{ countMedals }}</td>
                    <!-- <td>28</td>
                    <td>22</td>
                    <td>85</td> -->
                </tr>
        </table>
        <div class="container">
            <div class="country__buttons">
                <button @click="() => medalsSetup('gold')" class="btn"><img width="40" src="/medals/gold.png" alt="gold">Medals</button>
                <button @click="() => medalsSetup('silver')" class="btn"><img width="40" src="/medals/silver.png" alt="silver">Medals</button>
                <button @click="() => medalsSetup('bronze')" class="btn"><img width="40" src="/medals/bronze.png" alt="bronze">Medals</button>
            </div>
        </div>
    </main>
</template>

<style>
    .country__buttons {
        display: flex;
        flex-direction: column;
        gap: 10px;
    }

</style>
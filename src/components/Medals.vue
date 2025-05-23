<script setup>
import { onMounted, defineProps, inject, provide, watch, ref } from 'vue';

const route = inject('route');
const country = inject('country');
const medalsIt = inject('medalsIt');
const count = ref(0)

onMounted(() => {
    // console.log(country.value.disciplines.length, 'country.disciplines')
    for (let a = 0; a < country.value.disciplines.length; a++) {
        // console.log(a, 'd');
        // count.value = count.value + country.value.disciplines[a-1];
        // console.log(medalsIt.value.medal, 'medalsIt.medal')
        // console.log(country.value.disciplines[a][medalsIt.value.medal]);
        count.value = count.value + country.value.disciplines[a][medalsIt.value.medal]
    }
})
const countrySetup = (countryNewValue) => {
    console.log(countryNewValue);
    country.value = countryNewValue;
    route.value = 'country';
}

</script>

<template>
            <div class="main__content main--country container">
            <!-- <h1>{{ country }} e</h1> -->

            <!-- <img class="main__img-medails" src="/frame.png" alt="frame"> -->
            <h1 class="header__text">{{ country.name }}</h1>
            <img width="125" :src="country.flag" :alt="country.name">
            <!-- <div v-for="country in countries">
                <button @click="() => countrySetup(country)" class="btn"><img width="40" :src=country.flag :alt="country.name">{{country.name}}</button>
            </div> -->

        </div>
    <main class="container">
        <div class="main__content">
            <!-- <h1>{{ route }} e</h1> -->
            <div class="main__medals main__country">
                <h1 class="main__medals-text">{{ medalsIt.medal }} medals</h1>
                <p class="main__medals-count">{{ count }}</p>
            </div>
            <table class="country__table">
                <tr>
                    <th class="main__medals-td">DISCIPLINE</th>
                    <th class="main__medals-td">MEDALS</th>
                </tr>
                <!-- <tr> -->
                    <!-- <td v-for="count in country.medals">{{ count }}</td> -->
                    <tr class="main__medals-td" v-for="country in country.disciplines">
                        <td>{{ country.name }}</td>
                        <td>{{ country[medalsIt.medal] }}</td>
                    </tr>
                    <!-- <td class="main__medals-td" v-for="country in country.disciplines">{{ country.name }}</td> -->

                    <!-- <td>28</td>
                    <td>22</td>
                    <td>85</td> -->
                <!-- </tr> -->
        </table>
            <!-- <img class="main__img-medails" src="/frame.png" alt="frame"> -->
            <!-- <h1 class="header__text">Countries</h1>
            <div v-for="country in countries">
                <button @click="() => countrySetup(country)" class="btn"><img width="40" :src=country.flag :alt="country.name">{{country.name}}</button>
            </div> -->
        </div>
    </main>
</template>
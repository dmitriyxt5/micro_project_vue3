<script setup>
    import { inject, onMounted, computed, watch, toRaw } from 'vue';
    const discipline = inject('discipline');
    const countries = inject('countries');

    // const medal = computed(() => {
    //     const result = countries.value.map((val) => {

    //         const res = val.disciplines
    //         .filter((msg) => msg.name === discipline.value
    //         )
    //         .map((msg) => msg.name)
    //         const medals = val.medals.gold + val.medals.silver + val.medals.bronze;
    //         if (res[0]) {
    //             return {
    //             name: res[0], 
    //             city: val.name, 
    //             medal: medals,
    //         };
    //         }

    //     })
    //     return result.filter(Boolean);
    // })
    const cityCountry = JSON.parse(localStorage.getItem('cityCountry'));

    onMounted(() => {
        // console.log(medal.value, 'medal')
        console.log(cityCountry)

    })


    // const disciplines = computed(() => {
    //         const values = countries.value.flatMap((vals) => {
    //             console.log(vals, 'ds')
    //             const valueBack = vals.disciplines.map((val) => {
    //                 // console.log(val.name, 'val')
    //                 return val.name;
    //             })
    //             return valueBack;
    //         })
    //         // console.log(values, 'values')
    //         return [...new Set(values)];
    //     }
    // )
    // onMounted(() => {
    //     console.log(disciplines.value)

            
    // })//[0].disciplines

    
</script>

<template>
    <main class="container">
        <h1 class="main__disciplines main__disciplines--head">{{ discipline }}</h1>
        <img class="main__disciplines--big-logo" width="40" :src="`/disciplines/${discipline}.svg`" :alt="discipline">
        <p class="main__disciplines main__disciplines--p">{{ cityCountry.city }}</p>
        <!-- <div class="main__disciplines-list" v-for="discipline in disciplines">
            <button class="btn"><img width="40" :src="`/disciplines/${discipline}.svg`" alt="gold">{{ discipline }}</button>
        </div>  -->

    </main>
    <table class="table__disciplines">
        <tr>
            <td>GOLD</td>
            <td>SILVER</td>
            <td>BRONZE</td>
            <td>TOTAL</td>
        </tr>
        <tr >
            <th>{{cityCountry.inf.gold}}</th>
            <th>{{cityCountry.inf.silver}}</th>
            <th>{{cityCountry.inf.bronze}}</th>
            <th>{{cityCountry.total}}</th>

        </tr>
    </table>
    <!-- <table class="table table__disciplines">
        <tr>
            <th>Country</th>
            <th>Medals</th>
        </tr>
        <tr v-for="med in medal">
            <td>{{ med.city }}</td>
            <td>{{ med.medal }}</td>
        </tr>
    </table> -->
</template>

<style>
    .table__disciplines {
        /* display: flex; */
        /* justify-content: center; */
        gap: 20px;
        padding: 20px 20px;
        margin: 20px auto;
        width: 80%;
    }
    .table__disciplines th {
        padding: 0px 30px;
    }
    .main__disciplines--head {
        font-size: 48px;
        text-transform: uppercase;
    }
    .main__disciplines--p {
        font-size: 40px;
        text-transform: uppercase;

    }
    .main__disciplines {
        text-align: center;
        color: white;
        margin: 20px 0;
    }
    .main__disciplines-list {
        margin: 10px 0;
        overflow-y: scroll;
    }
    .main__disciplines--big-logo {
        width: 150px;
        display: flex;
        margin: 10px auto;

    }
</style>
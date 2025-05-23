<script setup>
    import { inject, onMounted, computed, watch, toRaw } from 'vue';
    const discipline = inject('discipline');
    const countries = inject('countries');
    const route = inject('route');

    const country = inject('country');
    const medal = computed(() => {
        const result = countries.value.map((val) => {

            const res = val.disciplines
            .filter((msg) => msg.name === discipline.value
            )
            .map((msg) => msg.name)
            const realMedals = val.disciplines.map((value) => {
                if (value.name === discipline.value) {
                    return {
                        gold: value.gold,
                        silver: value.silver,
                        bronze: value.bronze
                    };
                }
            }).filter(Boolean)
            console.log(realMedals, 'realMedals')
            const medals = realMedals.gold + realMedals.silver + realMedals.bronze;
            if (res[0]) {
                return {
                    name: res[0], 
                    city: val.name, 
                    medals: realMedals,
                    medalSum: medals,
                };
            }

        })
        return result.filter(Boolean);
    })

    onMounted(() => {
        console.log(medal.value, 'medal')
    })

    const DisciplineCountry = (city, inf, total) => {
        console.log(city, 'inform', inf, 'inf', total, 'total')
        localStorage.setItem('cityCountry', JSON.stringify({
            city: city,
            inf: inf[0],
            total: inf[0].gold + inf[0].silver + inf[0].bronze,
        }));
        route.value = 'DisciplineCountry';
    }


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

        <!-- <div class="main__disciplines-list" v-for="discipline in disciplines">
            <button class="btn"><img width="40" :src="`/disciplines/${discipline}.svg`" alt="gold">{{ discipline }}</button>
        </div>  -->

    </main>
    <table class="table table__disciplines">
        <thead>
        <tr>
            <th>Country</th>
            <th>Medals</th>
        </tr>
    </thead>
        <tr v-for="med in medal">
            <td class="clickable_td" @click="() => DisciplineCountry(med.city, med.medals, med.medalSum)">{{ med.city }}</td>
            <td>{{ med.medals[0].gold+med.medals[0].silver+med.medals[0].bronze }}</td>
        </tr>
    </table>
</template>

<style>
    .clickable_td {
        cursor: pointer;
        text-decoration: underline;
    }
    .clickable_td:hover {
        color: #00ff26;
    }
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
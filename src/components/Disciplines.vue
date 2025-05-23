<script setup>
    import { inject, onMounted, computed } from 'vue';
    const countries = inject('countries');
    const discipline = inject('discipline');
    const route = inject('route');

    const disciplines = computed(() => {
            const values = countries.value.flatMap((vals) => {
                console.log(vals, 'ds')
                const valueBack = vals.disciplines.map((val) => {
                    // console.log(val.name, 'val')
                    return val.name;
                })
                return valueBack;
            })
            // console.log(values, 'values')
            return [...new Set(values)];
        }
    )
    onMounted(() => {
        console.log(disciplines.value, 'd')

            
    })//[0].disciplines

    const setDiscipline = (val) => {
        // console.log(discipline)
        discipline.value = val;
        route.value = 'discipline';
    }
    
</script>

<template>
    <main class="container">
        <h1 class="main__disciplines">Disciplines</h1>
        <div class="main__disciplines-list" v-for="discipline in disciplines">
            <button  @click="() => setDiscipline(discipline)" class="btn"><img width="40" :src="`/disciplines/${discipline}.svg`" alt="discipline">{{ discipline }}</button>
        </div> 
    </main>
</template>

<style>
    .main__disciplines {
        text-align: center;
        color: white;
        margin: 20px 0;
    }
    .main__disciplines-list {
        margin: 10px 0;
        overflow-y: scroll;
    }
</style>
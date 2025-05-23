<script setup>
import Header from './components/Header.vue'
import MainHeader from './components/main_header.vue'
import Main from './components/Main.vue'
import Countries from './components/Countries.vue'
import Country from './components/Country.vue'
import Disciplines from './components/Disciplines.vue'
import Discipline from './components/Discipline.vue'
import DisciplineCountry from './components/DisciplineCountry.vue'

import Medals from './components/Medals.vue'

import { onMounted, ref, provide } from 'vue';


const country = ref('');
provide('country', country)
const medalsIt = ref('')
provide('medalsIt', medalsIt);
const countries = ref('');
onMounted(() => {
    fetch('http://localhost:3000/countries')
    .then(res=>res.json())
    .then(res => {
        console.log(res)
        countries.value = res
    })
    .catch(err => console.error(err))
})
provide('countries', countries)
const discipline = ref('')
provide('discipline', discipline);

const route = ref('default');
provide('route', route)
onMounted(() => {
  console.log(route.value)

})

const changeRoute = (newValue) => {
  route.value = newValue;
}
</script>

<template>
  <div class="main">
  <div v-if="route == 'default'">
    <MainHeader />
    <Main />
  </div>
  <div v-if="route == 'countries'">
    <Header />
    <Countries />
  </div>
  <div v-if="route == 'country'">
    <Header />
    <Country />
  </div>
  <div v-if="route == 'medals'">
    <Header />
    <Medals />
  </div>
  <div v-if="route == 'disciplines'">
    <Header />
    <Disciplines />
  </div>
  <div v-if="route == 'discipline'">
    <Header />
    <Discipline />
  </div>
  <div v-if="route == 'DisciplineCountry'">
    <Header />
    <DisciplineCountry />
  </div>
</div>

</template>

<style>
.main {
  background: url('/bg.png');
  background-size: 110%;
  background-position: -10px -10px;
  height: 100vh;

}
* {
  overflow-y: auto;
}
</style>
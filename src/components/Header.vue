<script setup>
    import { inject } from 'vue';

    const route = inject('route');

    const routeBack = () => {
        console.log(route.value, 'route')
        if (route.value == 'countries') {
            route.value = 'default';
        } else if (route.value == 'country') {
            route.value = 'countries';
        } else if (route.value == 'medals') {
            route.value = 'country';

        } else if (route.value == 'disciplines') {
            route.value = 'default';
        } else {
            route.value = 'default';
        }
    }
</script>

<template>
    <header class="header">
        <!-- <img src="/bg.png" alt="bg"> -->
         <!-- <h1>type</h1> -->
          <button @click="() => routeBack()">
            <img src="/ico-prev.svg" alt="prev icon">
          </button>
         <img src="/logo-sm-white.png" alt="ico white">
    </header>

    

    
</template>

<style scoped>
button {
    background: none;
    border: none;
}
    .header {
        display: flex;
        justify-content: space-between;
        padding: 30px 25px;
    }
</style>
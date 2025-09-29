<script setup>
import { RouterLink, RouterView } from 'vue-router';

import BarraNavegacao from './components/BarraNavegacao.vue';

import 'bootstrap/dist/css/bootstrap.min.css'
import './complements/style.css'
</script>

<template>
<BarraNavegacao></BarraNavegacao>
  
<RouterView></RouterView>
</template>

<style scoped>
</style>

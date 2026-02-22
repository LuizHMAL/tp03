<script setup lang="ts">
import { RouterView } from 'vue-router'
import RedirectableCard from './components/RedirectableCard.vue';
import HomeView from './views/HomeView.vue';
import Header from './components/Header.vue';
import Carrousel from './components/carrousel.vue';
</script>

<template>

  <Header />
  
  <div class="mainBody">
  <RedirectableCard titulo="Força bruta" content="Algoritmo de força bruta para encontrar soluções em problemas de otimização."/>
  <Carrousel />
    <!-- <RouterView /> -->
  </div>
</template>

<style scoped>
.mainBody {
  min-height: 100vh;
  display: flex;
  margin: 0 auto;
  gap: 2rem;
  flex-direction: column;
  justify-content: center;
  align-items: center; 
  color: #fff;
  background-color: #282c34;
}

</style>

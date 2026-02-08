<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <div class="mainBody">
    <h1>Hello World</h1>
    <RouterView />
  </div>
</template>

<style scoped>
.mainBody {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center; 
  color: #fff;
  background-color: #282c34;
}

</style>

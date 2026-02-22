<script setup lang="ts">
import { ref } from 'vue';

const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>


<template>
  <header class="header">
    <div class="logo">MyApp</div>
    <nav :class="{ 'open': isMenuOpen }">
      <a href="#">Home</a>
      <a href="#">About</a>
      <a href="#">Contact</a>
    </nav>
    <button class="menu-toggle" @click="toggleMenu">
      {{ isMenuOpen ? 'Close' : 'Menu' }}
    </button>
  </header>
</template>
<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
  background-color: #333;
  color: white;
}
.logo {
  font-size: 1.5rem;
  font-weight: bold;
}
nav {
  display: flex;
  gap: 1rem;
}
nav a {
  color: white;
  text-decoration: none;
}
.menu-toggle {
  display: none;
  background: none;
  border: 1px solid white;
  color: white;
  padding: 0.5rem 1rem;
  cursor: pointer;
}


</style>

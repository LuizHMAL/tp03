<script setup lang="ts">
    const props = defineProps({
    titulo: String ,  
    content: String
})

    const method = () => {
        console.log("Card clicado!");
    }
</script>

<template>
  <div class="card">
    <div class="card_title">
      {{ props.titulo }}
    </div>
    <div class="content">
       {{ props.content }}  
    </div>
  </div>
</template>

<style scoped>
.card {
  display: flex;
  flex-direction: column;
  width: 20rem;
  height: 15rem;
  border: 1px solid #ccc;
  border-radius: 1rem;
  padding: 10px;
  background-color: #fff;
  color: black;
  transition: box-shadow 0.2s ease, transform 0.1s ease;
 
}
.card_title {
  font-size: 1.2rem;
  font-weight: bold;
}
.card:hover {
  cursor: pointer;
  box-shadow: 0 4px 16px rgba(0,0,0,0.15);;
  transform: scale(1.02);
  transition: 0.3s;
}
.card:active {
  transform: scale(0.98);

} 
.content {
  margin: 0 auto;
  margin-top: 10px;
  margin-left: 16px;
  font-size: 0.9rem;
  color: #555;
}


</style>

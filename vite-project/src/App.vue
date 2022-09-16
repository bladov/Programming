<script setup>
import TheTitle from "./components/theTitle.vue";
import TheProgramm from "./components/theProgramm.vue";
import ThePracticue from "./components/thePracticue.vue";
</script>

<template>
  <div class="container">
    <header><TheTitle>Специализированные дисциплины</TheTitle></header>
    <main><TheProgramm /></main>
    <footer><ThePracticue /></footer>
  </div>
</template>

<style scoped>
body {
}
.container {
  margin: 0 auto;
  max-width: 1336px;
  padding: 0 25px;
}
</style>

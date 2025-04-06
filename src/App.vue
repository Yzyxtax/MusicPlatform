<script setup>
import HelloWorld from './components/HelloWorld.vue'
import index from './components/index.vue';
import Login from './page/login.vue';
</script>

<template>
  <div>
    <login></login>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>

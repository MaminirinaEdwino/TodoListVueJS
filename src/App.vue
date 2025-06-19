<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Content from './components/Content.vue';
</script>

<template>
  <Header></Header>
  <h3>All of your Todo is Here</h3>
  <Content></Content>
  <Footer></Footer>
</template>

<style scoped>
  h3{
    text-align: center;
    font-family: 'Courier New', Courier, monospace;
    color: #42b983;
    margin-top: 20px;
  }
</style>

<script setup>
import { ref } from "vue";
import Modal from "./components/Modal.vue";

const isModalOpen = ref(false);
</script>

<template>
  <button @click.prevent="isModalOpen = true">Open modal</button>
  <Modal :isModalOpen="isModalOpen" @close="isModalOpen = false" />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

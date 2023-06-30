<script setup>
import { ref } from "vue";
import Modal from './components/modal/Modal.vue';

const showModal = ref(false)
</script>

<template>
  <button @click="showModal = true">Show Modal</button>
  <Modal :show="showModal" @close="showModal = false">
    <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Tempora amet saepe natus ut magni corrupti placeat veritatis vitae magnam aliquid autem reprehenderit, aperiam id dolorem sint nisi totam, provident iure.</p>
  </Modal>
</template>
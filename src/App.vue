<script setup>
import { ref } from "vue";
import Modal from './components/modal/Modal.vue';

const showModal = ref(false)
</script>

<template>
  <div class="center">
    <button @click="showModal = true" class="btn btn-secondary">Show Modal</button>
  </div>
  <Modal :show="showModal" @close="showModal = false">
    <template v-slot:header>
      Modal title
    </template>
    <template v-slot:footer>
      <button class="btn btn-secondary" @click="showModal = false">Close</button>
      <button class="btn btn-primary">Save change</button>
    </template>
    <template v-slot:body>
      <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Tempora amet saepe natus ut magni corrupti placeat veritatis vitae magnam aliquid autem reprehenderit, aperiam id dolorem sint nisi totam, provident iure.</p>
    </template>
  </Modal>
</template>

<style>
.btn {
  cursor: pointer;
  outline: 0;
  display: inline-block;
  font-weight: 400;
  line-height: 1.5;
  text-align: center;
  padding: 6px 12px;
  font-size: 1rem;
  border-radius: 0.25rem;
  transition: color 0.15s ease-in-out, background-color 0.15s ease-in-out,
    border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}

.btn-primary {
  color: #fff;
  background-color: #0d6efd;
  border-color: #0d6efd;
  border: 1px solid transparent;
}
.btn-primary:hover {
  color: #fff;
  background-color: #0b5ed7;
  border-color: #0a58ca;
}

.btn-secondary {
  border: 1px solid transparent;
  color: #fff;
  background-color: #6c757d;
  border-color: #6c757d;
}

.btn-secondary:hover {
  color: #fff;
  background-color: #5c636a;
  border-color: #565e64;
}

p {
  padding: 0;
  margin: 0;
}

.center {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>
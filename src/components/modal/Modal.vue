<script setup>
defineProps({
    show: {
        type: Boolean,
        default: false
    }
})
</script>

<template>
    <div class="v-modal" :class="{ hidden: !show }">
        <div class="v-modal-dialog">
            <div class="v-modal-content">
                <slot />
                <button @click="$emit('close')" type="button">Close</button>
            </div>
        </div>
    </div>
</template>

<style scoped>
*,
::before,
::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.v-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow-x: hidden;
  overflow-y: auto;
  background-color: rgba(0, 0, 0, 0.4);
  z-index: 1;
}

.v-modal-dialog {
  max-width: 500px;
  margin: 2rem auto;
}

.v-modal-content {
  position: relative;
  background-color: #fff;
  border: 1px solid rgba(0, 0, 0, 0.3);
  background-clip: padding-box;
  border-radius: 0.3rem;
  padding: 1rem;
}

.hidden {
    display: none;
}
</style>
<script setup>
import { onMounted, onUnmounted } from "vue";
defineProps({
    show: {
        type: Boolean,
        default: false
    }
})

const emit = defineEmits(['close'])

const close = () => {
    emit('close')
}

const handleKeyup = (event) => {
    if (event.keyCode === 27) {
        close()
    }
}

onMounted(() => document.addEventListener('keyup', handleKeyup))
onUnmounted(() => document.removeEventListener('keyup', handleKeyup))
</script>

<template>
    <transition name="fade">
        <div class="v-modal" v-show="show" @click.self="close">
            <transition name="drop">
                <div class="v-modal-dialog" v-show="show">
                    <div class="v-modal-content">
                        <slot />
                        <button @click="close" type="button">Close</button>
                    </div>
                </div>
            </transition>
        </div>
    </transition>
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

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.drop-enter-active,
.drop-leave-active {
  transition: all 0.3s ease-out;
}

.drop-enter-from,
.drop-leave-to {
  opacity: 0;
  transform: translate(0, -50px);
}
</style>
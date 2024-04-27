<script setup>
import { ref } from 'vue';
import Button from './Button.vue'

defineProps({
  title: { type: String, required: true },
  text: { type: String, required: true }
})
const emit = defineEmits(['close'])

const animationClass = ref('fade-in')

function close() {
  animationClass.value = 'fade-out'
  setTimeout(() => {
    emit('close')
  }, 500)
}
</script>

<template>
  <div class="background" :class="animationClass" ref="bg"></div>
  <div class="popup" :class="animationClass">
    <div class="popup-close-icon" @click="close">
      <img src="../assets/close-icon.svg" alt="close" />
    </div>
    <div class="popup-title">{{ title }}</div>
    <div class="popup-text">{{ text }}</div>
    <Button class="popup-close-button" @click="close">
      Close
    </Button>
  </div>
</template>

<style scoped>
.background {
  position: fixed;
  top: 0;
  width: 100dvw;
  height: 100dvh;
  overflow: hidden;

  background: rgba(22, 44, 78, 0.6);
}

.popup {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  width: 320px;
  height: 370px;
  padding: 28px 24px 24px;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 28px;
  
  background-color: #FFFFFF;
  border: 1px solid rgba(19, 89, 120, 0.07);
  border-radius: 2px;
}

.popup-title {
  font-family: 'Poppins';
  font-style: normal;
  font-weight: 700;
  font-size: 36px;
  line-height: 104%;
  text-align: center;
  text-transform: uppercase;

  color: #162C4E;
}

.popup-text {
  font-family: 'Poppins';
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 150%;
  text-align: center;

  color: rgba(0, 0, 0, 0.8);
}

.popup-close-button {
  padding: 16px 72px;
}

.popup-close-icon {
  position: absolute;
  top: 24px;
  right: 16px;
  cursor: pointer;
}

.fade-in {
  animation-name: fade-in;
  animation-duration: 500ms;
}

.fade-out {
  animation-name: fade-out;
  animation-duration: 500ms;
  opacity: 0;
}

@keyframes fade-in {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@keyframes fade-out {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
</style>
<script setup>
defineProps({
  number: { type: Number, required: true },
  text: { type: String, required: true }
})
</script>

<template>
  <div>
    <div class="timer-number-font">{{ number }}</div>
    <div class="text">{{ text }}</div>
  </div>
</template>

<style scoped>
.text {
  background-image: url('../assets/timer-number-bg.png');
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;

  display: flex;
  align-items: center;
  justify-content: center;

  padding: 40px;
  margin-top: -20px;

  font-family: 'Poppins';
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 100%;

  color: #FFFFFF;
}

@media screen and (max-width: 1060px) {
  .text {
    font-size: 12px;
    padding: 24px;
  }
}
</style>
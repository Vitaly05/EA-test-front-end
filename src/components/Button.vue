<script setup>
defineEmits(['click'])
</script>

<template>
  <button class="button" @click="$emit('click')">
    <div class="button-content">
      <slot />
      <slot name="icon" />
    </div>
  </button>
</template>

<style scoped>
.button {
  padding: 10px 20px;
  border-radius: 40px;
  
  font-family: 'Poppins';
  font-style: normal;
  font-weight: 400;
  font-size: 18px;
  line-height: 150%;
  
  background-color: #1D4169;
  color: #FFFFFF;

  border: none;
  cursor: pointer;

  transition: background-color 200ms;
}
.button:hover {
  background-color: #183557;
}

.button-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 28px;
}
</style>
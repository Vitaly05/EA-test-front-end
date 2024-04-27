<script setup>
defineEmits(['click'])
</script>

<template>
  <button class="button" @click="$emit('click')">
    <div class="button-content">
      <slot />
    </div>
  </button>
</template>

<style scoped>
.button {
  padding: 12px 28px;

  font-family: 'SF Pro Text';
  font-style: normal;
  font-weight: 600;
  font-size: 18px;
  line-height: 120%;
  
  background-color: transparent;
  color: #FFFFFF;
  border: 2px solid rgba(255, 255, 255, 0.8);
  border-left-width: 8px;

  cursor: pointer;

  transition: background-color 200ms;
}
.button:hover {
  background-color: #232323;
}

.button-content {
  display: flex;
  align-items: center;
  justify-content: center;
}

@media screen and (max-width: 1770px) {
  .button {
    font-size: 16px;
  }
}
</style>
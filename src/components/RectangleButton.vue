<script setup>
defineEmits(['click'])
</script>

<template>
  <button class="button" @click="$emit('click')">
    <div class="line"></div>
    <div class="button-content">
      <slot />
    </div>
  </button>
</template>

<style scoped>
.button {
  position: relative;
  padding: 12px 28px;
  z-index: 2;

  font-family: 'SF Pro Text';
  font-style: normal;
  font-weight: 600;
  font-size: 18px;
  line-height: 120%;
  
  background-color: transparent;
  border: 2px solid rgba(255, 255, 255, 0.8);

  cursor: pointer;

  transition: background-color 200ms;
}
.button:hover .button-content {
  color: #162C4E;
}

.button:hover .line {
  width: 100%;
}

.line {
  position: absolute;
  width: 8px;
  height: 100%;
  left: 0;
  top: 0;
  z-index: 1;

  transition: width 500ms;

  background-color: rgba(255, 255, 255, 0.8);
}

.button-content {
  position: relative;
  z-index: 3;

  display: flex;
  align-items: center;
  justify-content: center;

  color: #FFFFFF;

  transition: color 500ms;
}

@media screen and (max-width: 1770px) {
  .button {
    font-size: 16px;
  }
}
</style>
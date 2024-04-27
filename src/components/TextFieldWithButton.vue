<script setup>
defineProps({
  placeholder: { type: String, required: false }
})
defineEmits(['click'])
const value = defineModel()
</script>

<template>
  <div style="position: relative;">
    <input 
      class="text-field default-font"
      :placeholder="placeholder"
      v-model="value"
    />
    <button @click="$emit('click')">
      <img src="../assets/arrow.svg" alt="arrow" />
    </button>
  </div>
</template>

<style scoped>
.text-field {
  outline: none;

  background-color: #FFFFFF;
  border: 1px solid rgba(0, 0, 0, 0.8);
  box-shadow: 0px 0px 50px rgba(0, 0, 0, 0.4);
  border-radius: 40px;

  padding: 10px 20px;
  width: 100%;

  transition: background-color 200ms;
}
.text-field:focus {
  background-color: #e2e2e2;
}
.text-field::placeholder {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  font-size: 18px;
  line-height: 150%;

  color: rgba(0, 0, 0, 0.6);
}

button {
  padding: 10px;
  border-radius: 40px;

  display: flex;
  align-items: center;
  justify-content: space-between;
  
  background-color: #DF2224;

  border: none;
  cursor: pointer;

  position: absolute;
  top: 50%;
  right: 4px;
  transform: translate(0, -50%);

  transition: background-color 200ms;
}
button:hover {
  background-color: #b61c1e;
}


@media screen and (max-width: 1060px) {
  .text-field::placeholder {
    font-size: 14px;
  }
}
</style>
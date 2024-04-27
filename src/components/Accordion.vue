<script setup>
import { ref } from 'vue';
import AccordionItem from './AccordionItem.vue'

defineProps(['items'])

const activeIndex = ref(1)

let lastClickTime

function setActiveIndex(index) {
  if (!lastClickTime) {
    lastClickTime = new Date()
    activeIndex.value = index
  } else {
    const clickTime = new Date()
    if (clickTime - lastClickTime > 1000) {
      activeIndex.value = index
      lastClickTime = clickTime
    }
  }
}
</script>

<template>
  <div class="accordion">
    <AccordionItem 
      v-for="(event, index) in items"
      :index="index + 1"
      :title="event.title"
      :description="event.description"
      :image-src="event.imageSrc"
      :link="event.link"
      :is-active="index + 1 === activeIndex"
      @click="setActiveIndex"
    />
  </div>
</template>

<style scoped>
.accordion {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 2px;
}


@media screen and (max-width: 1770px) {
  .accordion {
    flex-direction: column;
    width: 688px;
  }
}

@media screen and (max-width: 767px) {
  .accordion {
    width: 90%;
  }
}
</style>
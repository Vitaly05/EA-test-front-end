<script setup>
import { ref } from 'vue';
import Accordion from './components/Accordion.vue'

const events = [
  {
    title: 'Hawaiian party',
    description: '13.02.2023',
    imageSrc: 'Hawaiian party.jpg',
    link: 'https://example.com'
  },
  {
    title: 'Mafia party',
    description: '13.02.2023',
    imageSrc: 'Mafia party.jpg',
    link: 'https://example.com'
  },
  {
    title: 'Party',
    description: '13.02.2023',
    imageSrc: 'Party.jpg',
    link: 'https://example.com'
  },
  {
    title: 'Party on the beach',
    description: '13.02.2023',
    imageSrc: 'Party on the beach.jpg',
    link: 'https://example.com'
  },
  {
    title: 'Home Security',
    description: '13.02.2023',
    imageSrc: 'Party on the beach.jpg',
    link: 'https://example.com'
  },
  {
    title: 'Network Design & Implementation',
    description: '13.02.2023',
    imageSrc: 'Network Design & Implementation.jpg',
    link: 'https://example.com'
  },
  {
    title: 'System Design & Engineering',
    description: '13.02.2023',
    imageSrc: 'System Design & Engineering.jpg',
    link: 'https://example.com'
  },
  {
    title: 'Client Care Plans',
    description: '13.02.2023',
    imageSrc: 'Client Care Plans.jpg',
    link: 'https://example.com'
  }
]
</script>

<template>
  <div class="full-page-container" id="all-events">
    <div class="title-font">All events</div>
    <div class="accordion-panel">
      <Accordion :items="events" />
    </div>
  </div>
</template>

<style scoped>
.full-page-container {
  position: relative;
  width: 100dvw;
  height: auto;
  min-height: 100dvh;
  overflow-x: hidden;
  padding: 40px 0;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 40px;
}

.accordion-panel {
  display: flex;
  justify-content: center;
  width: 100%;
}
</style>
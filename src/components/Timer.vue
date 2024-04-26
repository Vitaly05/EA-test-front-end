<script setup>
import { onUnmounted, ref } from 'vue'
import TimerNumber from './TimerNumber.vue'

const TARGET_DATE = new Date(2024, 6, 24)

const time = ref({
  days: {
    value: 92, text: 'Days'
  },
  hours: {
    value: 11, text: 'Hours'
  },
  minutes: {
    value: 41, text: 'Minutes'
  },
  seconds: {
    value: 48, text: 'Seconds'
  }
})

function calculateTime() {
  const currentDate = new Date()

  const remainingMilliseconds = TARGET_DATE - currentDate

  const oneSecond = 1000
  const oneMinute = oneSecond * 60
  const oneHour = oneMinute * 60
  const oneDay = oneHour * 24

  time.value.days.value = Math.floor(remainingMilliseconds / oneDay)
  time.value.hours.value = Math.floor((remainingMilliseconds % oneDay) / oneHour)
  time.value.minutes.value = Math.floor((remainingMilliseconds % oneHour) / oneMinute)
  time.value.seconds.value = Math.floor((remainingMilliseconds % oneMinute) / oneSecond)
}
calculateTime()

const timeInterval = setInterval(() => {
  calculateTime()
}, 1000)

onUnmounted(() => {
  clearInterval(timeInterval)
})

function handleResize() {
  if (window.innerWidth <= 1060) {
    time.value.days.text = 'DD'
    time.value.hours.text = 'HH'
    time.value.minutes.text = 'MM'
    time.value.seconds.text = 'SS'
  } else {
    time.value.days.text = 'Days'
    time.value.hours.text = 'Hours'
    time.value.minutes.text = 'Minutes'
    time.value.seconds.text = 'Seconds'
  }
}

handleResize()
window.addEventListener('resize', handleResize);
</script>

<template>
  <div class="timer">
    <TimerNumber :number="time.days.value" :text="time.days.text" />
    <div class="timer-number-font">:</div>
    <TimerNumber :number="time.hours.value" :text="time.hours.text" />
    <div class="timer-number-font">:</div>
    <TimerNumber :number="time.minutes.value" :text="time.minutes.text" />
    <div class="timer-number-font">:</div>
    <TimerNumber :number="time.seconds.value" :text="time.seconds.text" />
  </div>
</template>

<style scoped>
.timer {
  display: flex;
  justify-content: center;
  gap: 14px;
  width: auto;
  height: auto;
}

@media screen and (max-width: 1060px) and (min-width: 530px) {
  .timer {
    gap: 10px;
  }
}

@media screen and (max-width: 530px) {
  .timer {
    gap: 4px;
  }
}
</style>
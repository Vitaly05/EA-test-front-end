<script setup>
import Button from './components/Button.vue'
import Timer from './components/Timer.vue'
import SubscribePanel from './components/SubscribePanel.vue'
</script>

<template>
  <div class="full-page-container">
    <img src="./img/bg-left.png" id="bg-left-vector" class="slide-ltr" style="animation-delay: 500ms;" />
    <img src="./img/bg-right.png" id="bg-right-vector" class="slide-rtl" style="animation-delay: 500ms;" />

    <div class="logo slide-down">
      <a href="/">
        <img src="./img/logo.png" alt="Lead Advisors" />
      </a>
    </div>
    <div class="content">
      <div class="top-text slide-down" style="animation-delay: 400ms;">
        <div class="title-font">Under Construction</div>
        <div class="default-font text-center">We're making lots of improvements and will be back soon</div>
      </div>
      <div class="timer slide-down" style="animation-delay: 500ms;">
        <Timer />
      </div>
      <div class="events slide-down" style="animation-delay: 600ms;">
        <div class="default-font">Check our event page when you wait:</div>
        <a href="https://example.com" target="_blank">
          <Button>
            Go to the event
            <template #icon>
              <img src="./img/arrow.svg" alt="arrow" />
            </template>
          </Button>
        </a>
      </div>
    </div>

    <SubscribePanel class="subscribe-panel" />
  </div>
</template>

<style scoped>
.full-page-container {
  position: relative;
  width: 100dvw;
  height: 100dvh;
  overflow-x: hidden;
}

.logo {
  height: 20%;
  display: flex;
  align-items: center;
  justify-content: center;
}
.logo img {
  width: 190px;
}

.content {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  width: 100%;
  height: 65%;
}

.top-text {
  display: flex;
  flex-direction: column;
  align-items: center;
  max-width: 90%;
}
.top-text div:nth-child(2) {
  margin-top: 10px;
  width: 420px;
  max-width: 90%;
}

.timer {
  margin-top: 40px;
}

.events {
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px
}

#bg-left-vector,
#bg-right-vector {
  position: absolute;
  z-index: -1;
}

#bg-left-vector {
  width: 400px;
}

#bg-right-vector {
  right: 0;
  width: 300px;
}


@media screen and (max-width: 1060px) and (min-width: 530px) {
  #bg-left-vector {
    width: 260px;
    top: -20px;
    left: -20px;
  }
  #bg-right-vector {
    width: 220px;
    right: -24px;
  }

  .top-text div:nth-child(2) {
    max-width: 70%;
  }
}

@media screen and (min-width: 1060px) and (max-height: 840px) {
  .top-text div:nth-child(2) {
    margin-top: 5px;
  }
  .timer {
    margin-top: 10px;
  }
  .events {
    margin-top: 10px;
  }

  #bg-left-vector {
    width: 260px;
    top: -20px;
    left: -20px;
  }
  #bg-right-vector {
    width: 220px;
    right: -24px;
  }
}

@media screen and (max-width: 530px) {
  #bg-left-vector {
    width: 200px;
    top: -26px;
    left: -26px;
  }
  #bg-right-vector {
    width: 180px;
    right: -40px;
  }

  .logo > img {
    width: 128px;
  }

  .top-text div:nth-child(2) {
    width: 286px;
  }

  .timer {
    margin-top: 20px;
  }
  .events {
    margin-top: 20px;
  }
}
</style>

<style>
.subscribe-panel {
  width: 100%;
  height: 15%;
}
</style>
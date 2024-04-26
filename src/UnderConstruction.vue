<script setup>
import Button from './components/Button.vue'
import Timer from './components/Timer.vue'
import SubscribePanel from './SubscribePanel.vue'
</script>

<template>
  <div class="container">
    <img src="./img/bg-right.png" id="bg-right-vector" />
    <img src="./img/bg-left.png" id="bg-left-vector" />

    <a class="logo" href="/">
      <img src="./img/logo.png" alt="Lead Advisors" />
    </a>
    <div class="content">
      <div class="top-text">
        <div class="title-font">Under Construction</div>
        <div class="default-font text-center">We're making lots of improvements and will be back soon</div>
      </div>
      <Timer style="margin-top: 40px;" />
      <div class="events">
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

    <SubscribePanel />
  </div>
</template>

<style scoped>
.container {
  position: relative;
  width: 100dvw;
  height: 100dvh;
  overflow: hidden;
}

.logo {
  height: 20%;
  display: flex;
  align-items: center;
  justify-content: center;
}
.logo > img {
  width: 190px;
}

.content {
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
}
</style>
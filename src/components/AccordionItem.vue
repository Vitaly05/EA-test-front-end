<script setup>
import { computed } from 'vue';
import RectangleButton from './RectangleButton.vue'

defineEmits(['click'])

const props = defineProps({
  index: { type: Number, required: true },
  title: { type: String, required: true },
  description: { type: String, required: false },
  imageName: { type: String, required: true },
  link: { type: String, required: true },
  isActive: { type: Boolean, required: true }
})

const stringIndex = computed(() => {
  return props.index < 10 ? `0${props.index}` : props.index
})
</script>

<template>
  <div class="item" :class="{ active: isActive }">
    <div class="side-panel" @click="$emit('click', index)">
      <div class="title">
        {{ title }}
      </div>
      <div class="index">
        {{ stringIndex }}
      </div>

      <div class="background-image" :style="{ backgroundImage: `url('/src/img/${imageName}')`}"></div>
      <div class="background"></div>
      <div class="line"></div>
    </div>
    <div class="main-panel" :style="{ backgroundImage: `url('/src/img/${imageName}')`}">
      <div class="background"></div>
      <div class="info">
        <div class="title">{{ title }}</div>
        <div v-if="description" class="description">{{ description }}</div>
        <div class="actions">
          <a :href="link" target="_blank">
            <RectangleButton style="width: 100%;">
              More information
            </RectangleButton>
          </a>
        </div>
      </div>

      <div class="index">{{ stringIndex }}</div>
      <div class="line"></div>
    </div>
  </div>
</template>

<style scoped>
.item {
  height: 682px;
  display: flex;
  gap: 2px;
}

.side-panel {
  position: relative;
  height: 100%;
  width: 85px;
  overflow: hidden;

  display: flex;
  flex-direction: column;
  justify-content: end;
  align-items: center;
  gap: 40px;
  padding-bottom: 20px;

  background-color: #162C4E;

  cursor: pointer;
}

.item.active .side-panel {
  cursor: auto;
}

.item.active .side-panel .background,
.item.active .side-panel .background-image {
  opacity: 0;
}

.line {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  z-index: 5;

  border: 2px solid #DF2224;
  box-shadow: 0px 0px 10px #FF1E00;
}

.side-panel .background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 2;

  background: linear-gradient(180deg, rgba(22, 44, 78, 0) 0%, #162C4E 100%);

  transition: opacity 1000ms;
}

.side-panel .background-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;

  background: rgba(18, 18, 18, 0.7);
  background-blend-mode: darken;
  background-size: cover;
  background-position: center;

  transition: opacity 1000ms;
}

.side-panel .title {
  font-family: 'SF Pro Text';
  font-style: normal;
  font-weight: 600;
  font-size: 32px;

  z-index: 5;
  
  writing-mode: vertical-lr;
  transform: rotate(180deg);

  color: #FFFFFF;
}

.side-panel .index {
  font-family: "SF Pro Text";
  font-style: normal;
  font-weight: 500;
  font-size: 40px;
  letter-spacing: -0.03em;
  color: #FFFFFF;
  z-index: 5;
}

.main-panel {
  position: relative;
  width: 0;
  overflow: hidden;

  background-color: rgba(18, 18, 18, 0.8);
  background-size: 995px auto;
  background-position-y: center;
  background-repeat: no-repeat;

  transition: width 1000ms linear, height 1000ms linear;
}

.item.active .main-panel {
  height: 100%;
  width: 995px;
}

.main-panel .info {
  width: 364px;
  height: 100%;

  display: flex;
  flex-direction: column;
  justify-content: end;
  padding: 52px;

  background: rgba(18, 18, 18, 0.8);
  backdrop-filter: blur(20px);
}

.main-panel .title {
  font-family: 'SF Pro Text';
  font-style: normal;
  font-weight: 600;
  font-size: 24px;
  line-height: 120%;
  color: #FFFFFF;
}

.main-panel .description {
  margin-top: 12px;

  font-family: 'SF Pro Text';
  font-style: normal;
  font-weight: 300;
  font-size: 18px;
  line-height: 150%;

  color: rgba(255, 255, 255, 0.8);
}

.main-panel .actions {
  margin-top: 24px;
}

.main-panel .index {
  position: absolute;
  top: 0;
  left: -160px;

  font-family: 'SF Pro Text';
  font-style: normal;
  font-weight: 600;
  font-size: 380px;
  letter-spacing: -0.03em;

  color: rgba(255, 255, 255, 0.04);
}


@media screen and (max-width: 1770px) {
  .item {
    height: auto;
    width: 100%;
    flex-direction: column-reverse;
  }

  .side-panel {
    height: 85px;
    width: 100%;

    flex-direction: row-reverse;
    justify-content: start;
    gap: 30px;
    padding-left: 20px;
    padding-bottom: 0;
  }

  .side-panel .title {
    font-size: 24px;
    
    writing-mode: horizontal-tb;
    transform: rotate(0);
  }

  .side-panel .index {
    font-size: 32px;
  }

  .main-panel {
    display: flex;
    align-items: end;
    width: 100%;
    height: 0;

    background-size: 100% auto;
    background-position-y: top;
  }

  .item.active .main-panel {
    height: 460px;
    width: 100%;
  }

  .main-panel .info {
    width: 100%;
    height: 192px;
    
    justify-content: start;
    align-items: start;
    padding: 25px;
  }

  .main-panel .title {
    font-size: 18px;
  }

  .main-panel .description {
    font-size: 16px;
  }

  .main-panel .index {
    top: auto;
    left: auto;
    bottom: 28px;
    right: -28px;

    font-size: 152px;
  }
}
</style>
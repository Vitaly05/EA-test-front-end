<script setup>
import { ref } from 'vue';
import TextFieldWithButton from './TextFieldWithButton.vue'
import Popup from './Popup.vue'
import * as yup from 'yup'

const API_URL = 'example.com'

const emailSchema = yup
  .string()
  .email()
  .required()

const email = ref('')
const isPopupOpen = ref(false)
const isError = ref(false)
const errorMessage = ref('')

function subscribeEmail() {
  isError.value = false
  if (emailSchema.isValidSync(email.value)) {
    sendEmail()
  } else {
    isError.value = true
    errorMessage.value = 'You entered an invalid email address'
    isPopupOpen.value = true
  }
}

function sendEmail() {
  const formData = new FormData()
  formData.append('email', email.value)

  let xhr = new XMLHttpRequest()
  xhr.open('POST', API_URL, true)
  xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')
  xhr.send(formData)
  xhr.onload = () => {
    if (xhr.status !== 200) {
      isError.value = true
      errorMessage.value = 'An error occurred while sending an email'
    }
    isPopupOpen.value = true
  }
}

function scrollToEvents() {
  document.getElementById('all-events').scrollIntoView({
    behavior: 'smooth',
    block: 'start'
  })
}
</script>

<template>
  <div class="panel" :class="$attrs.class">
    <TextFieldWithButton 
      placeholder="Enter your Email and get notified"
      id="email-field"
      v-model="email"
      @click="subscribeEmail"
    />
    <div class="other-events" @click="scrollToEvents">
      <div class="text">Other Events<hr></div>
      <img src="../assets/arrow.svg" alt="arrow" />
    </div>
  </div>

  <Teleport to="body">
    <Popup 
      v-if="isPopupOpen && !isError"
      title="Success!"
      text="You have successfully subscribed to the email newsletter"
      @close="isPopupOpen = false"
    />
    <Popup 
      v-else-if="isPopupOpen && isError"
      title="Error!"
      :text="errorMessage"
      @close="isPopupOpen = false"
    />
  </Teleport>
</template>

<style scoped>
.panel {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  
  background-color: #162C4E;
}

#email-field {
  width: 440px;
}

.other-events {
  position: absolute;
  right: 110px;
  padding: 8px;

  display: flex;
  align-items: center;
  gap: 14px;

  cursor: pointer;
}

.other-events:hover img {
  transform: rotate(270deg);
}

.other-events:hover .text > hr {
  width: 100%;
  border-color: #FFFFFF;
}

.other-events .text > hr {
  width: 0;
  border-color: transparent;

  transition: width 500ms, border-color 500ms;
}

.other-events .text {
  font-family: 'Poppins';
  font-style: normal;
  font-weight: 400;
  font-size: 20px;
  line-height: 150%;
  
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  color: #FFFFFF;
}

.other-events img {
  transform: rotate(90deg);

  transition: transform 500ms;
}


@media screen and (max-width: 1060px) {
  #email-field {
    width: 360px;
  }

  .panel {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 16px;
  }

  .other-events {
    position: relative;
    right: auto;
    padding: 0;
  }

  .other-events .text {
    font-size: 16px;
  }
}

@media screen and (max-width: 530px) {
  #email-field {
    width: 280px;
  }
}
</style>
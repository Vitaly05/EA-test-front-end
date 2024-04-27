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
</script>

<template>
  <div class="panel" :class="$attrs.class">
    <TextFieldWithButton 
      placeholder="Enter your Email and get notified"
      id="email-field"
      v-model="email"
      @click="subscribeEmail"
    />
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
  display: flex;
  align-items: center;
  justify-content: center;
  
  background-color: #162C4E;
}

#email-field {
  width: 440px;
}


@media screen and (max-width: 1060px) and (min-width: 530px) {
  #email-field {
    width: 360px;
  }
}

@media screen and (max-width: 530px) {
  #email-field {
    width: 280px;
  }
}
</style>
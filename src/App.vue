<template>
  <div>
    <div class="container">
      <captcha :user-input-for-passphrase="userInput"
               @right-passphrase="grantAccess"
               @wrong-passphrase="showErrorMessage = true"/>
      <form @submit.prevent="userInput = inputVal">
        <input type="text" v-model="inputVal" @input="showErrorMessage = false">
        <button type="Submit">Submit</button>
      </form>
    </div>
    <div v-if="hasAccess">
      Special Secret :)
    </div>
    <div v-if="showErrorMessage">
      Wrong passphrase, try again!
    </div>
  </div>
</template>

<script>

import Captcha from '@/components/Captcha'

export default {
  name: 'App',
  components: { Captcha },
  data () {
    return {
      inputVal: '',
      userInput: '',
      hasAccess: false,
      showErrorMessage: false
    }
  },
  methods: {
    grantAccess () {
      this.hasAccess = true
    }
  }
}
</script>

<style scoped lang="sass">
.container
  display: flex
  align-items: center
</style>

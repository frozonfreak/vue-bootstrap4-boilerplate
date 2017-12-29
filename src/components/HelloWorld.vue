<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <b-alert :show="dismissCountDown"
             dismissible
             variant="warning"
             @dismissed="dismissCountdown=0"
             @dismiss-count-down="countDownChanged">
      This alert will dismiss after {{dismissCountDown}} seconds...
    </b-alert>
    <b-alert variant="primary"
             dismissible
             :show="showPrimaryDismissibleAlert"
             @dismissed="showPrimaryDismissibleAlert=false">
      Primary Alert!
    </b-alert>
    
    <b-alert variant="secondary"
             dismissible
             :show="showSecondaryDismissibleAlert"
             @dismissed="showSecondaryDismissibleAlert=false">
      Secondary Alert!
    </b-alert>

    <b-alert variant="success"
             dismissible
             :show="showSuccessDismissibleAlert"
             @dismissed="showSuccessDismissibleAlert=false">
      Success Alert!
    </b-alert>

    <b-alert variant="danger"
             dismissible
             :show="showDangerDismissibleAlert"
             @dismissed="showDangerDismissibleAlert=false">
      Danger Alert!
    </b-alert>

    <b-alert variant="warning"
             dismissible
             :show="showWarningDismissibleAlert"
             @dismissed="showWarningDismissibleAlert=false">
      Warning Alert!
    </b-alert>
  
    <b-alert variant="info"
             dismissible
             :show="showInfoDismissibleAlert"
             @dismissed="showInfoDismissibleAlert=false">
      Info Alert!
    </b-alert>

    <b-alert variant="light"
             dismissible
             :show="showLightDismissibleAlert"
             @dismissed="showLightDismissibleAlert=false">
      Light Alert!
    </b-alert>

    <b-alert variant="dark"
             dismissible
             :show="showDarkDismissibleAlert"
             @dismissed="showDarkDismissibleAlert=false">
      Dark Alert!
    </b-alert>

    <b-btn @click="showAlert" variant="info" class="m-1">
      Auto Close Notification
    </b-btn>
    <b-btn @click="showPrimaryDismissibleAlert=true" variant="info" class="m-1">
      Primary
    </b-btn>
    <b-btn @click="showSecondaryDismissibleAlert=true" variant="info" class="m-1">
      Secondary
    </b-btn>
    <b-btn @click="showSuccessDismissibleAlert=true" variant="info" class="m-1">
      Success
    </b-btn>
    <b-btn @click="showDangerDismissibleAlert=true" variant="info" class="m-1">
      Danger
    </b-btn>
    <b-btn @click="showWarningDismissibleAlert=true" variant="info" class="m-1">
      Warning
    </b-btn>
    <b-btn @click="showInfoDismissibleAlert=true" variant="info" class="m-1">
      Info
    </b-btn>
    <b-btn @click="showLightDismissibleAlert=true" variant="info" class="m-1">
      Light
    </b-btn>
    <b-btn @click="showDarkDismissibleAlert=true" variant="info" class="m-1">
      Dark
    </b-btn>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      dismissSecs: 10,
      dismissCountDown: 0,
      showPrimaryDismissibleAlert: false,
      showSecondaryDismissibleAlert: false,
      showSuccessDismissibleAlert: false,
      showDangerDismissibleAlert: false,
      showWarningDismissibleAlert: false,
      showInfoDismissibleAlert: false,
      showLightDismissibleAlert: false,
      showDarkDismissibleAlert: false
    }
  },
  methods: {
    countDownChanged (dismissCountDown) {
      this.dismissCountDown = dismissCountDown
    },
    showAlert () {
      this.dismissCountDown = this.dismissSecs
    }
  }
}
</script>
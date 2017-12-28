<template>
  <div class="app">    
    <transition name="fade"
                mode="out-in">
      <router-view></router-view>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'app',
  methods: {
    handleOpen (key, keyPath) {
      console.log(key, keyPath)
    },
    handleClose (key, keyPath) {
      console.log(key, keyPath)
    },
    routeTo (routeName, param) {
      this.$router.push({name: routeName, params: { text: param }})
    }
  }
}
</script>

<style lang="scss">
  @import './assets/scss/main';
</style>

<template>
  <div>
    <Main/>
  </div>
</template>

<script>
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Main
  }
}
</script>

<style lang="scss">
@import './assets/style/global.scss';
div{
  font-family: 'Roboto', sans-serif;
}
</style>

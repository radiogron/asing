<template>
  <div id="app">
    <Predictions/>
  </div>
</template>

<script>
import Predictions from './components/Predictions.vue'

export default {
  name: 'App',
  components: {
  Predictions
  }
}
</script>

<style lang="sass">
html, body
  margin: 0
  padding: 0
  line-height: 1.5
*
  box-sizing: border-box
#app
  padding: 0
</style>

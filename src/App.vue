<template>
  <div id="app">
      <song-display></song-display>
  </div>
</template>

<script>
import SongDisplay from './components/SongDisplay.vue'
export default {
  name: 'App',
  components: {
    SongDisplay
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

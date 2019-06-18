<template>
  <div id="app">
    <Quiz></Quiz>
  </div>
</template>

<script>
import Quiz from './components/quiz/Quiz.vue' TEST ADD

export default {
  name: 'app',
  components: {
    Quiz
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100%;
  max-width: 750px;
  margin: 0 auto;
  height: 100%;
}
</style>

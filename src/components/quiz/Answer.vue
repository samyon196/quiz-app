<template>
  <div class="answer">
    {{text}}
  </div>
</template>

<script>
export default {
  name: 'Answer',
  props: {
      text : String,
      isCorrect: Boolean
  }
}
</script>

<style>
.answer {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color: #05ff00;
  width: 50%;
  margin: auto auto;
}
</style>
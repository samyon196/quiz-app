<template>
  <div id="question">
    {{text}}
  </div>
</template>

<script>
export default {
  name: 'Question',
  props: {
      text : String
  }
}
</script>

<style>
#question {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color: #ffff00;
  width: 50%;
  margin: auto auto;
}
</style>
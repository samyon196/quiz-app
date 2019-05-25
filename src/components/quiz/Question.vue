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

<style scoped>
@import url(http://fonts.googleapis.com/css?family=Raleway:400,500,700);
#question {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color: #eae1ee;
  width: 100%;
  margin: 15px auto;
  padding: 10px;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2);
  background-color: #f8f8f8;
  color: #000000;
  font-weight: bold;
  font-size: 1em;
  font-family: 'Raleway', Arial, sans-serif;
  box-sizing: border-box;
}
</style>
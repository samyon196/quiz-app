<template>
  <div class="answer" @click="setBackground" :style="{'border-left-color': activeColor}">
    {{text}}, {{correct}}
  </div>
</template>

<script>
export default {
  name: 'Answer',
  data: function() {
    return {
      activeColor: '#f8f8f8'
    }
  },
  methods: {
    setBackground: function() {
      if(this.correct) {
        this.activeColor = '#55ff55';
      }
      else {
        this.activeColor = '#ff3333';
      }
    }
  },
  props: {
      text : String,
      correct: Boolean,
      reset: Boolean
  }
}
</script>

<style scoped>
@import url(http://fonts.googleapis.com/css?family=Raleway:400,500,700);
.answer {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color: #ffffff;
  width: 85%;
  margin: 5px auto;
  padding: 5px;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2);
  background-color: #f8f8f8;
  color: #74777b;
  font-weight: regular;
  font-size: 1em;
  font-family: 'Raleway', Arial, sans-serif;
  box-sizing: border-box;
  border-left: 25px solid;
  border-left-color: blue;
  transition: all 1.5s ease-in-out;
}
</style>
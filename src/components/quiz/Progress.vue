<template>
    <div>
        <div v-if="isAnswered">
            <strike>Question <b>{{currentQuestion+1}}/{{num_questions}}</b></strike> <span style="font-size: 0.7em">(Question {{realIndex+1}})</span>
        </div>
        <div v-else>
            Question <b>{{currentQuestion+1}}/{{num_questions}}</b> <span style="font-size: 0.7em">(Question {{realIndex+1}})</span>
        </div>
        <progress :value="currentQuestion+1" :max="num_questions"></progress><br />
        <progress :value="correctNum" :max="correctNum+incorrectNum" id='correct'></progress><br />

        <div>Correct: <b>{{correctNum}}</b>, Incorrect: <b>{{incorrectNum}} [{{correctPrec}}%]</b></div>
    </div>
</template>

<script>
/*

        */
export default {
  name: 'Progress',
  props: {
      currentQuestion : Number,
      num_questions : Number,
      realIndex : Number,
      correctNum : Number,
      incorrectNum : Number,
      isAnswered : Boolean
  },
    computed: {
    correctPrec: function() {
      var c = (100*this.correctNum/(this.correctNum+this.incorrectNum));
      if(isNaN(c)) {
        c = (0);
      }
      return Math.ceil(c);
    }
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
progress, progress[role] {
    transition: all 0.5s ease;
    box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2);
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    border: none;
    background-size: auto;
    height: 10px;
    width: 100%;
    background-color: #d3d3d3;
    margin: 3px;
  }
  progress::-moz-progress-bar {
    background: rgb(151, 68, 228);

  }
  progress::-webkit-progress-bar {
      background: transparent;
  }  
  progress::-webkit-progress-value {  
    background: rgb(151, 68, 228);
  }
  #correct, #correct[role] {
    background-color: #990e0e;
  }
  #correct::-moz-progress-bar {
    background-color: green;
  }
  #correct::-webkit-progress-value {
    background-color: green;
  }
</style>
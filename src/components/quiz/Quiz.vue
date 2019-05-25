<template>
  <div id="quiz">
    <b>Welcome to the Samyon&Lior Quiz system! :)</b> <br /><br /><br />
    Question <b>#{{currentQuestion+1}}/{{num_questions}}</b><br />
    <progress :value="currentQuestion+1" :max="num_questions"></progress><br /><br />
    <Question :text="questionsFile.questions[currentQuestion].question"></Question>
    <Answer :text="questionsFile.questions[currentQuestion].answers[0]" correct></Answer>
    <Answer :text="questionsFile.questions[currentQuestion].answers[1]" ></Answer>
    <Answer :text="questionsFile.questions[currentQuestion].answers[2]" ></Answer>
    <Answer :text="questionsFile.questions[currentQuestion].answers[3]" ></Answer>
    <Answer :text="questionsFile.questions[currentQuestion].answers[4]" ></Answer>
    <button @click="nextQuestion">Next Question</button>
  </div>
</template>

<script>
import QFile from '../../assets/questions.json';
import Question from './Question.vue'
import Answer from './Answer.vue'

export default {
  name: 'Quiz',
  data: function () {
    return {
      questionsFile: QFile,
      currentQuestion:0,
    }
  },
  methods: {
    nextQuestion: function() {
      if(this.currentQuestion+1 < this.num_questions) {
        this.currentQuestion++;
      }
      else {
        alert('Test finished!');
      }
    }
  },
  computed: {
    num_questions: function () {
        return this.questionsFile.questions.length;
    }
  },
  components: {
    Question,
    Answer
  }
}
</script>

<style>
#quiz {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

progress, progress[role] {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  border: none;
  background-size: auto;
  height: 10px;
  width: 50%;
}

</style>
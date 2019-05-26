<template>
  <div id="quiz">
    <img src="../../assets/test.png" alt="Test icon" style="width:128px;height:128px;"><br />
    <Progress :isAnswered="isAnswered[currentQuestion]" :currentQuestion="currentQuestion" :num_questions="num_questions" :realIndex="questionIdxArray[currentQuestion]" :correctNum="correctNum" :incorrectNum="incorrectNum"></Progress>
    <Question :text="questionsFile.questions[questionIdxArray[currentQuestion]].question"></Question>
    <div v-if="renderAns">
        <div v-for="i in ansIdxArray" :key="i">
          <Answer @selected="setAnswered" v-if="i == 0" :text="ansArr[i]" correct :reveal="currReveal || isAnswered[currentQuestion]"></Answer>
          <Answer @selected="setAnswered" v-else :text="ansArr[i]" :reveal="currReveal || isAnswered[currentQuestion]"></Answer>
        </div>
    </div>
    <button @click="prevQuestion">Prev Question</button>
    <button @click="nextQuestion">Next Question</button>
    <footer >
      Samyon&Lior 2019 Quiz system.
    </footer> 
  </div>
</template>

<script>
import QFile from '../../assets/questions.json';
import Question from './Question.vue'
import Answer from './Answer.vue'
import Progress from './Progress.vue'

export default {
  name: 'Quiz',
  data: function () {
    return {
      questionsFile: QFile,
      currentQuestion:0,
      correctNum: 0,
      incorrectNum: 0,
      isAnswered: [],
      questionIdxArray: [],
      ansIdxArray: [],
      renderAns: true,
      currReveal: false
    }
  },
  mounted: function() {
    // Setup array for questionMix:
    this.questionIdxArray = this.shuffle([...Array(this.num_questions).keys()]);
    this.ansIdxArray = this.shuffle([...Array(5).keys()]);
    this.isAnswered = new Array(this.num_questions).fill(false);
  },
  methods: {
    setAnswered: function(isCorrect) {
      if(!this.isAnswered[this.currentQuestion]) {
        this.isAnswered[this.currentQuestion] = true;
        if(isCorrect) {
          this.correctNum++;
          this.currReveal = true;
        }
        else {
          this.incorrectNum++;
        }
      }
    },
    prevQuestion: function() {
      if(this.currentQuestion-1 >= 0) {
        this.currentQuestion--;
        this.ansIdxArray = this.shuffle([...Array(5).keys()]);
      }
      else {
        return;
      }
      this.currReveal = false;
      this.renderAns = false;
      this.$nextTick(() => {
        this.renderAns = true;
      });
    },
    nextQuestion: function() {
      if(this.currentQuestion+1 < this.num_questions) {
        this.currentQuestion++;
        this.ansIdxArray = this.shuffle([...Array(5).keys()]);
      }
      else {
        alert('Test finished!');
      }
      this.currReveal = false;
      this.renderAns = false;
      this.$nextTick(() => {
        this.renderAns = true;
      });
    },
    shuffle: function(a) {
      for (let i = a.length - 1; i > 0; i--) {
          const j = Math.floor(Math.random() * (i + 1));
          [a[i], a[j]] = [a[j], a[i]];
      }
      return a;
    }
  },
  computed: {
    num_questions: function () {
        return this.questionsFile.questions.length;
    },
    ansArr: function() {
      return this.questionsFile.questions[this.questionIdxArray[this.currentQuestion]].answers;
    }
  },
  components: {
    Question,
    Answer,
    Progress
  }
}
</script>

<style scoped>
  #quiz {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    border: none;
    background-color: #fff;
    box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2);
    width: 100%;
    margin: 0 auto;
    box-sizing: border-box;
    border-left: 10px solid rgb(151, 68, 228);
    transition: all 0.5s ease;
    padding: 15px 15px 0px 15px;
    color: rgb(133, 133, 133);
    background-color: #f8f8f8;
    height: 100%;
  }
  
  button {
    background-color: #8800ff; /* Green */
    border: none;
    color: white;
    padding: 15px 10px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    cursor: pointer;
    box-shadow: 0 3px 5px 0 rgba(0, 0, 0, 0.5);
    font-weight: 200;
    margin-top: 15px;
  }
  footer {
    font-size: 0.6em;
    margin-top: 15px;
    text-align: left;
  }
</style>
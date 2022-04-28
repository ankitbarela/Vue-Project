<template>
  <div class="question-box-container">
    <b-jumbotron>
      <template #lead>
        {{ currentQuestion.question }}
      </template>

      <hr class="my-4" />

      <b-list-group>
        <b-list-group-item
          v-for="(answer,index) in answers"
          :key="answer"
          @click="selectAnswer(index)"
          :class="[selectedIndex === index ? 'selected' : '']"
        >
          {{ answer }}</b-list-group-item
        >
      </b-list-group>

      <b-button variant="primary" href="#">Submit</b-button>
      <b-button variant="success" @click="Next" href="#">Next</b-button>
    </b-jumbotron>
  </div>
</template>


<script>
import _ from 'lodash'
export default {
  name: "QuestionComponent",
  props: {
    currentQuestion: Object,
    Next: Function,
  },
  data(){
      return {
          selectedIndex : null,
          suffledAnswers : []
      }
  },
  watch:{
      currentQuestion:{
          immediate : true,
            handler(){
                 this.selectedIndex = null
                 this.suffleAnswer()
            }
      }
    //   currentQuestion(){
    //       this.selectedIndex = null
    //       this.suffleAnswer()
    //   }
  },
  methods: {
    selectAnswer(index) {
        this.selectedIndex = index
      console.warn(index)
    },
    suffleAnswer(){
      let answers = [...this.currentQuestion.incorrect_answers ,this.currentQuestion.correct_answer];
        this.suffledAnswers = _.shuffle(answers)
    }
  },
  computed: {
    answers() {
      let answers = [...this.currentQuestion.incorrect_answers];
      answers.push(this.currentQuestion.correct_answer);
      return answers;
    },
  },
};
</script>

<style scoped>
.list-group-item:hover{
    background-color: #EEE;
}

.selected {
    background-color: lightblue;
}
.correct {
    background-color: yellow;
}
.incorrect {
    background-color: red;
}
</style>
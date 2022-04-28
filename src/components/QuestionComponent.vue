<template>
  <div class="question-box-container">
    <b-jumbotron>
      <template #lead>
          {{currentQuestion.question}}
      </template>

      <hr class="my-4" />

      <p>
        List Of Questions
      </p>

      <b-button variant="primary" href="#">Submit</b-button>
      <b-button variant="success" @click="Next" href="#">Next</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  name: "QuestionComponent",
 props : {
      currentQuestion : Object,
      Next : Function
 }
};
</script>
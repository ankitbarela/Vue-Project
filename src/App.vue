<template>
  <div id="app">
    <header-component 
    :numCorrect ="numCorrect" 
    :numTotal ="numTotal"  />
    <b-container>
      <b-row>
        <b-col sm="6" offset="3">
          <question-component v-if="questionText.length" :currentQuestion= questionText[index] 
           :Next=nextClick 
           :increment =increment
           />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import QuestionComponent from "./components/QuestionComponent.vue";

export default {
  name: "App",
  components: {
    HeaderComponent,
    QuestionComponent,
  },
  data(){ 
    return {
      questionText : [],
      index : 0,
      numCorrect : 0 ,
      numTotal : 0 
    }
  },
methods : {
  nextClick(){
    this.index++
  },
  increment(isCorrect){
    if(isCorrect){
      this.numCorrect++
    }
    this.numTotal++
  }
},
  mounted(){
    fetch('https://opentdb.com/api.php?amount=10&category=27&type=multiple',{
      method: 'get'
    })
    .then((response) =>{
      return response.json()
    })
    .then((jsonData)=>{
      this.questionText = jsonData.results;
      console.warn(this.questionText)
    })
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

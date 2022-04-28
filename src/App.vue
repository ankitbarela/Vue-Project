<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <header-component/>
    <question-component/>
  </div>
</template>

<script>
import  HeaderComponent from './components/HeaderComponent.vue'
import  QuestionComponent from './components/QuestionComponent.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    QuestionComponent
  }
}
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

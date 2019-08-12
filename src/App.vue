<template>
  <div id="app"> 
    <!-- <h1>Hello !</h1> -->
    <question></question>
  </div>
</template>

<script>
import question from './components/question.vue'

export default {
  name: 'app',
  components: {
    question
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
</style>

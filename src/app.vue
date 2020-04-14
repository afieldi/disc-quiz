<template>
  <div id="app" class="bg-light">
    <!-- <h1>My Vue App</h1> -->
    <start :style="{display: startDisplay}"></start>
    <questions :style="{display: questionDisplay}"></questions>
    <results :discMost="resultMost" v-bind:discLeast="resultLeast" :style="{display: resultDisplay}"></results>
  </div>
</template>

<script>
import Start from './components/start.vue'
import Questions from './components/questions.vue'
import Results from './components/results.vue'
export default {
  name: 'appmain',
  components: {
    Start,
    Questions,
    Results
  },
  data: function() {
    return {
      startDisplay: 'block',
      questionDisplay: 'none',
      resultDisplay: 'none',
      resultMost: {},
      resultLeast: {},
    }
  },
  methods: {
    startQuiz ( ) {
      this.startDisplay = 'none';
      this.questionDisplay = 'block';
      this.resultDisplay = 'none';
    },
    submitQuiz ( mosts, leasts ) {
      this.resultMost = mosts;
      this.resultLeast = leasts;
      this.startDisplay = 'none';
      this.questionDisplay = 'none';
      this.resultDisplay = 'block';
    }
  }
}
</script>

<style>
#app {
  font-family: Helvetica, Arial, sans-serif;
  color: #2c3e50;
  height: 100vh;
}

.bg-dark { 
  background-color: #360707 !important;
}
</style>
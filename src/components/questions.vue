<template>
  <div class="container">
    <div class="grid-test">
      <div v-for="(question, index) in questions" :key="index" class="question-box">
        <div class="index-num text-primary">{{index + 1}}</div>
        <div v-for="(item, iindex) in question" :key="iindex">
          <div class="radio-sep-left"><input type="radio" v-bind:name="`most-${index}`" id="" :value="item.attribute"></div>
          <div class="radio-sep-right"><input type="radio" v-bind:name="`least-${index}`" id="" :value="item.attribute"></div>
          {{item.text}}
        </div>

      </div>
    </div>
    <br>
    <button type="button" class="btn btn-primary btn-custom" @click="submitAnswers()">Submit</button>
  </div>
</template>

<script>
import QuestionJson from '../assets/questions.json'
export default {
  data: function ( ) {
    return {
      questions: QuestionJson.data
    }
  },
  methods: {
    submitAnswers: function ( ) {
      var mosts = {
        "D": 0,
        "I": 0,
        "S": 0,
        "C": 0
      }
      var leasts = {
        "D": 0,
        "I": 0,
        "S": 0,
        "C": 0
      }

      var numQuestions = QuestionJson.data.length;
      for ( var i = 0; i < numQuestions; i ++ ) {
        var valM = $(`input[name=most-${i}]:checked`).val()
        if ( undefined == valM ) {
          alert(`In question ${i + 1} you did not fill out the most radio button`);
          return;
        }
        mosts[valM] += 1

        var valL = $(`input[name=least-${i}]:checked`).val()
        if ( undefined == valL ) {
          alert(`In question ${i + 1} you did not fill out the least radio button`);
          return;
        }
        leasts[valL] += 1
        
        // if (valL === valM) {
        //   alert(`In question ${i + 1} you had the same answer for most and least. Please change.`);
        //   return;
        // }
      }
      this.$parent.submitQuiz(mosts, leasts);
    }
  }
}
</script>

<style scoped>
.question-box {
  padding: 10px;
  border-bottom: 1px black solid;
}

.radio-sep-left {
  padding-right: 3px;
  display: inline-block;
  
}
.radio-sep-right {
  padding-left: 3px;
  display: inline-block;
  border-left: 1px black solid;
}

.index-num {
  font-size: 2em;
}

.btn-custom {
  left: 33.5%;
  position: relative;
  width: 33%;
  margin-bottom: 30px;
}

.grid-test {
  display: grid;
}
@media (max-width: 1199px) and (min-width: 900px){
  .grid-test {
    grid-template-columns: auto auto;
  }
}

@media (min-width: 1200px) {
  .grid-test {
    grid-template-columns: auto auto auto;
  }
}
</style>
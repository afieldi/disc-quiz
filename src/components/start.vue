<template>
  <div style="height: 100%">
    <div class="full-centered">
      <h1 class="title-style">DISC Personality Quiz</h1>
      <br><br>
      <button type="button" class="btn btn-primary full-centered" v-on:click="$parent.startQuiz()">Start</button>
      <div class="question-box small-container">
        <div class="index-num text-primary">1</div>
        <div>
          <div class="radio-sep-left"><input type="radio" v-bind:name="`test`" id="" :value="0"></div>
          <div class="radio-sep-right"><input type="radio" v-bind:name="`test2`" id="" :value="0"></div>
          Personality Attributes 1
        </div>
        <div>
          <div class="radio-sep-left"><input type="radio" v-bind:name="`test`" id="" :value="0"></div>
          <div class="radio-sep-right"><input type="radio" v-bind:name="`test2`" id="" :value="0"></div>
          Personality Attributes 2
        </div>
        <div>
          <div class="radio-sep-left"><input type="radio" v-bind:name="`test`" id="" :value="0"></div>
          <div class="radio-sep-right"><input type="radio" v-bind:name="`test2`" id="" :value="0"></div>
          Personality Attributes 3
        </div>
        <div>
          <div class="radio-sep-left"><input type="radio" v-bind:name="`test`" id="" :value="0"></div>
          <div class="radio-sep-right"><input type="radio" v-bind:name="`test2`" id="" :value="0"></div>
          Personality Attributes 4
        </div>
      </div>
      <p class="small-container">
        <br>
        <b class="text-primary">Instructions</b>
        <br>
        Select two options in each question. The left radio button is for the personality attribute you feel most reflects you, 
        and the right radio button is for the attribute you feel least reflects you. 
      </p>
    </div>
  </div>
</template>

<script>
export default {
  
}
</script>

<style scoped>
  .full-centered {
    position: relative;
    top: 30%;
    left: 50%;
    transform: translateX(-50%);
  }

  .title-style {
    text-align: center;
  }
  
  .btn {
    width: 20%;
  }
  @media (min-width: 600px) {
    .small-container {
      width: 33%;
      left: 33%;
      position: relative;
    }
  }
  .question-box {
    padding: 10px;
    /* width: 33%; */
    position: relative;
    border: 1px black solid;
    margin-top: 30px;
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
</style>
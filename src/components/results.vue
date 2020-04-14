<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <br><br><br>
        <h2 class="display-4">Your DISC Style: <b>{{styleBlend}}</b></h2>
        <hr>

        <p class="lead">
          <a class="btn btn-primary btn-lg" v-bind:href="styleURL" role="button">Learn more</a>
          <a class="btn btn-primary btn-lg" href="./" role="button">Take Again</a>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import Scores from '../assets/scores.json'
export default {
  props: [
    "discMost",
    "discLeast"
  ],
  methods: {

  },
  computed: {
    styleBlend: function ( ) {
      var blend = []
      for ( var key in this.discLeast ) {
        var mp = Scores.basic.midpoints[key]
        if ( this.discLeast[key] <= mp ) {
          blend.push({
            "key": key,
            "value": this.discLeast[key]
          })
        }
      }
      function customSort ( a, b ) {
        if ( a.value > b.value )
          return 1
        if ( a.value < b.value )
          return -1
        return 0
      }
      blend.sort(customSort);
      var styleStr = ""
      if ( blend.length > 0 ) {
        styleStr += blend[0].key
        for ( var i in blend ) {
          if ( i == 0 )
            continue
          if ( i == 1 )
            styleStr += "/"
          styleStr += blend[i].key
        }
      }
      return styleStr
    },
    styleURL: function ( ) {
      var t = this.styleBlend.replace('/', '');
      t = t.slice(0, 2).toLowerCase();
      return `https://www.discprofiles.com/blog/2019/what-is-the-disc-${t}-style/`
    }
  }
}
</script>

<style scoped>
.btn-lg {
  margin: 0 10px;
}
</style>
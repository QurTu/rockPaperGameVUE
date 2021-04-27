<template>

  <div class="scoreboard">
    <div class="logo">
      <img src="../assets/img/logo.svg" alt="">
    </div>
    <div class="scoreboard-itself">
      <h1>SCORE</h1>
      <p>{{score}}</p>
    </div>

  </div>
</template>

<script>

export default {
  name: 'ScoreBoard',
  data: function () {
    return {}
  },
  props: ['score']
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.scoreboard {
  display: flex;
  justify-content: space-between;
  border: 3px #fff solid;
  border-radius: 20px;
  width: 80%;
  margin: 0 auto;
  margin-top: 50px;
  padding: 0 50px;
}

img {
  height: 90%;
  width: auto;
  object-fit: contain;
  margin-top: 5%;
}
</style>

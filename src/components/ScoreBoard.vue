<template>

  <div class="scoreboard">
    <div class="logo">
      <img src="../assets/img/logo.svg" alt="">
    </div>
    <div class="scoreboard-itself">
      <h1>SCORE</h1>
      <p v-bind:class= " score >= 0 ? 'green' : 'red'">{{score}}</p>
    </div>
  </div>
</template>

<script>

export default {
  name: 'ScoreBoard',
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
  align-items: center;
}
img {
  height: 90%;
  width: auto;
  object-fit: contain;
  margin-top: 5%;
}
.scoreboard-itself {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.scoreboard-itself p {
  margin-top: 5px;
  font-weight: bold;
  color: #fff;
}
.scoreboard-itself h1 {
  font-weight: bold;
  color: #fff;
}
.green {
  color: green !important;
}
.red {
  color: red !important;
}
@media (max-width: 550px) {
  .scoreboard {
    flex-direction: column;
    padding-top: 30px;
    padding-bottom: 30px;
  }
  img {
    display: none;
  }
}
</style>

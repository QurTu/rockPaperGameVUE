<template>
 <score-board :score="score"> </score-board>
  <game-board @game-outcome="gameOutCome">  </game-board>
  <rules-button> </rules-button>


</template>

<script>
import GameBoard from './components/GameBoard.vue'
import ScoreBoard from './components/ScoreBoard.vue'
import RulesButton from './components/RulesButton'

export default {
  name: 'App',
  components: {
    GameBoard, ScoreBoard, RulesButton
  },
  data() {
    return {
      score: 0,
      }
    },
  methods: {
    gameOutCome(gameResult) {
      this.score += gameResult;
    },
    scoreUpdate() {
      this.score++
    }
  }
}
</script>

<style>
#app {

}
body,
body * {
  margin: 0;
  padding: 0;
  vertical-align: top;
  box-sizing: border-box;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  word-break: break-all;
}

*:focus {
  outline: none;
}
body {
  background-image: radial-gradient(hsl(214, 47%, 23%),hsl(237, 49%, 15%));
}

</style>

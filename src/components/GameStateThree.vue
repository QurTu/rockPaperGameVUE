<template>
  <div class="game-state-three">
    <div class="game-outcome">
      <h1 v-if="result == 1"> YOU WIN</h1>
      <h1 v-if="result == 0"> DRAWN GAME</h1>
      <h1 v-if="result == -1"> YOU LOSE</h1>
    </div>
    <div class="game-state-three-grid">
      <div class="your-pick">
        <img v-if="stageOnePick == 'paper'" src="../assets/img/icon-paper.svg" alt=""
             class="stage-one-paper pick-background">
        <img v-if="stageOnePick == 'rock'" src="../assets/img/icon-rock.svg" alt=""
             class="stage-one-rock pick-background">
        <img v-if="stageOnePick == 'scissors'" src="../assets/img/icon-scissors.svg" alt=""
             class="stage-one-scissors pick-background">
      </div>
      <div  class="pc-pick">
        <img v-if="pcPicks == 'paper'" src="../assets/img/icon-paper.svg" alt=""
             class="stage-one-paper pick-background">
        <img v-if="pcPicks == 'rock'" src="../assets/img/icon-rock.svg" alt=""
             class="stage-one-rock pick-background">
        <img v-if="pcPicks == 'scissors'" src="../assets/img/icon-scissors.svg" alt=""
             class="stage-one-scissors pick-background">
      </div>
    </div>
    <div class="play-again">
      <button @click="playAgain()" type="button"> PLAY AGAIN!</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "GameStateThree",
  emits: ["play-again"],
  props: ['result', 'stageOnePick',  'pcPicks'],
  methods: {
    playAgain()  {
      this.$emit('play-again');
    }
  }
}
</script>

<style scoped>

</style>
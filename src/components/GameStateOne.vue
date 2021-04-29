<template>
  <div class="game-state-one">
  <img class="game-state-one-triangle" src="../assets/img/bg-triangle.svg" alt="">
  <img @click="playerPick('paper')" src="../assets/img/icon-paper.svg" alt="" class="stage-one-paper pick-background">
  <img @click="playerPick('rock')" src="../assets/img/icon-rock.svg" alt="" class="stage-one-rock pick-background">
  <img @click="playerPick('scissors')" src="../assets/img/icon-scissors.svg" alt=""
       class="stage-one-scissors pick-background">
  </div>
</template>

<script>
export default {
  name: "GameStateOne",
  emits: ["player-pick"],
  methods: {
    playerPick(pick) {
      this.$emit('player-pick', pick );
    }
  }
}
</script>

<style scoped>

</style>
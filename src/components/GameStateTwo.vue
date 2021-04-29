<template>
  <div class="game-state-two">
    <div class="your-pick">
      <img v-if="playerPick == 'paper'" src="../assets/img/icon-paper.svg" alt=""
           class="stage-one-paper pick-background">
      <img v-if="playerPick == 'rock'" src="../assets/img/icon-rock.svg" alt=""
           class="stage-one-rock pick-background">
      <img v-if="playerPick == 'scissors'" src="../assets/img/icon-scissors.svg" alt=""
           class="stage-one-scissors pick-background">
    </div>
    <div @click="pcPick()" class="pc-pick">
      <img src="../assets/img/klaustukas.png" alt="" class="what-pc-picks pick-background">
    </div>

  </div>
</template>

<script>
export default {
  name: "GameStateTwo" ,
  emits: ["pc-pick"],
  props: ['playerPick'],
  methods: {
    pcPick() {
      this.$emit('pc-pick');
    }
  }
}
</script>

<style scoped>

</style>
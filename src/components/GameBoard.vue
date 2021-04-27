<template>
  <div v-if="gameState == 1" class="game-state-one">
    <img class="game-state-one-triangle" src="../assets/img/bg-triangle.svg" alt="">
    <img @click="playerPick('paper')" src="../assets/img/icon-paper.svg" alt="" class="stage-one-paper pick-background">
    <img @click="playerPick('rock')" src="../assets/img/icon-rock.svg" alt="" class="stage-one-rock pick-background">
    <img @click="playerPick('scissors')" src="../assets/img/icon-scissors.svg" alt=""
         class="stage-one-scissors pick-background">
  </div>
  <div v-if="gameState == 2" class="game-state-two">
    <div class="your-pick">
      <img v-if="stageOnePick == 'paper'" src="../assets/img/icon-paper.svg" alt=""
           class="stage-one-paper pick-background">
      <img v-if="stageOnePick == 'rock'" src="../assets/img/icon-rock.svg" alt=""
           class="stage-one-rock pick-background">
      <img v-if="stageOnePick == 'scissors'" src="../assets/img/icon-scissors.svg" alt=""
           class="stage-one-scissors pick-background">
    </div>
    <div @click="pcPick()" class="pc-pick">
      <img src="../assets/img/klaustukas.png" alt="" class="what-pc-picks pick-background">
    </div>

  </div>
  <div v-if="gameState == 3" class="game-state-three">
    <div class="game-outcome">
      <h1> YOU WIN</h1>
      <h1> DRAWN GAME</h1>
      <h1> YOU LOSE</h1>
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
      <div @click="pcPick()" class="pc-pick">
        <img v-if="pcPicks == 'paper'" src="../assets/img/icon-paper.svg" alt=""
             class="stage-one-paper pick-background">
        <img v-if="pcPicks == 'rock'" src="../assets/img/icon-rock.svg" alt=""
             class="stage-one-rock pick-background">
        <img v-if="pcPicks == 'scissors'" src="../assets/img/icon-scissors.svg" alt=""
             class="stage-one-scissors pick-background">
      </div>
    </div>
  </div>

</template>

<script>
export default {
  name: 'ScoreBoard',
  data() {
    return {
      stageOnePick: ' ',
      gameState: 1,
      pcPicks: ' ',
      result: null
    }
  },
  methods: {
    playerPick(pick) {
      this.stageOnePick = pick;
      this.gameState = 2;
    },
    pcPick() {
      let number = Math.floor(Math.random() * 3);
      if (number == 0) this.pcPicks = 'paper'
      if (number == 1) this.pcPicks = 'rock'
      if (number == 2) this.pcPicks = 'scissors'
      this.gameOutCome();
      this.gameState = 3;
    },
    gameOutCome() {
      switch(this.pcPicks) {
        case 'paper':
          if( this.stageOnePick == 'rock') this.result = -1
          if( this.stageOnePick == 'paper') this.result = 0
          if( this.stageOnePick == 'scissors') this.result = 1
                break;
        case 'rock':
          if( this.stageOnePick == 'rock') this.result = 0
          if( this.stageOnePick == 'paper') this.result = 1
          if( this.stageOnePick == 'scissors') this.result = -1
          break;
        case 'scissors':
          if( this.stageOnePick == 'rock') this.result = 1
          if( this.stageOnePick == 'paper') this.result = -1
          if( this.stageOnePick == 'scissors') this.result = 0
          break;

      }
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.game-state-one {
  position: relative;
  display: inline-block;
  width: 300px;
  margin: 100px calc(50vw - 150px);
}

.game-state-one .game-state-one-triangle {
  width: 300px;
}

.stage-one-paper {
  top: -75px;
  right: -75px;
  border: 10px solid red;
}

.stage-one-rock {
  bottom: -75px;
  left: calc(50% - 75px);
  border: 10px solid green;
}

.stage-one-scissors {
  top: -75px;
  left: -75px;
  border: 10px solid blue;
}

.game-state-two {
  position: absolute;
  margin-top: 100px;
  justify-content: center;
  display: flex;
  width: 800px;
  margin: 100px calc(50vw - 400px);

}
.game-state-three {
  position: absolute;
  margin-top: 100px;
  width: 800px;
  margin: 100px calc(50vw - 400px);
}
.game-state-three-grid {
  display: flex;
  justify-content: center;

}

.game-state-two img , .game-state-three img {
  margin: 0 50px;
  position: static;
}
</style>
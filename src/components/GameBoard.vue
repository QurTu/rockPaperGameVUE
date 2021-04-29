<template>
  <GameStateOne v-if="gameState == 1"  @player-pick="playerPick">   </GameStateOne>
  <GameStateTwo :playerPick="stageOnePick" v-if="gameState == 2"  @pc-pick="botPick">  </GameStateTwo>
  <GameStateThree v-if="gameState == 3" @play-again="playAgain" :result="result" :stageOnePick="stageOnePick" :pcPicks="pcPicks">    </GameStateThree>
</template>

<script>
import  GameStateOne from "./GameStateOne";
import GameStateTwo from "@/components/GameStateTwo";
import GameStateThree from "@/components/GameStateThree";
export default {
  name: 'ScoreBoard',
  components: {GameStateOne, GameStateTwo, GameStateThree},
  emits: ["game-outcome"],
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
    botPick() {
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
          if( this.stageOnePick == 'rock') this.result = -1;
          if( this.stageOnePick == 'paper') this.result = 0;
          if( this.stageOnePick == 'scissors') this.result = 1;
                break;
        case 'rock':
          if( this.stageOnePick == 'rock') this.result = 0;
          if( this.stageOnePick == 'paper') this.result = 1;
          if( this.stageOnePick == 'scissors') this.result = -1;
          break;
        case 'scissors':
          if( this.stageOnePick == 'rock') this.result = 1;
          if( this.stageOnePick == 'paper') this.result = -1;
          if( this.stageOnePick == 'scissors') this.result = 0;
          break;
      }
      this.$emit('game-outcome', this.result );
    },
    playAgain() {
      this.gameState = 1;

    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
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
.pick-background {
  cursor: pointer;
  background-color: white;
  height: 150px;
  width: 150px;
  position: absolute;
  object-fit: contain;
  padding: 25px;
  border-radius: 50%;
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
.game-state-three .game-outcome h1 {
  text-align: center;
  margin-bottom: 50px;
  color: #ffffff;
}
.play-again {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}
.play-again button {
  cursor: pointer;
  padding: 10px 20px;
  font-weight: bold;
}
@media (max-width: 550px) {
  .game-state-one {
    margin: 50px calc(50vw - 75px);
    width: 150px;
  }
  .game-state-one .game-state-one-triangle {
    width: 150px;
  }
  .stage-one-paper {
    top: -32.5px;
    right: -32.5px;
    border: 5px solid red;
  }

  .stage-one-rock {
    bottom: -32.5px;
    left: calc(50% + -32.5px);
    border: 5px solid green;
  }

  .stage-one-scissors {
    top: -32.5px;
    left: -32.5px;
    border: 5px solid blue;
  }
  .pick-background {
    cursor: pointer;
    background-color: white;
    height: 75px;
    width: 75px;
    position: absolute;
    object-fit: contain;
    padding: 15px;
    border-radius: 50%;
  }
  .game-state-two {
    margin-top: 50px;
  }
  .game-state-three {
  margin-top: 50px;
}
}
</style>
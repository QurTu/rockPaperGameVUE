<template>

  <button @click="RulesOpens()" class="rules-button"> RULES</button>
  <div v-show="rulesOpen == true" @click="wrapperClicked($event)" class="rules-wrapper" id="rules-wrapper">
    <div class="rules">
      <div @click="closeRules()" class="close-rules">x</div>
      <img src="../assets/img/image-rules.svg" alt="">
    </div>
  </div>

</template>

<script>



export default {
  name: "RulesButton",
  components: {},
  data() {
    return {
      rulesOpen: false,
    }
  },
  methods: {
    RulesOpens() {
      this.rulesOpen = true;
    },
    closeRules() {
      this.rulesOpen = false;
    },
    wrapperClicked(e) {
      if(e.target == document.getElementById("rules-wrapper")) this.rulesOpen = false;

    }
  }
}
</script>

<style scoped>
.rules-button {
  cursor: pointer;
  bottom: 50px;
  padding: 10px 20px;
  position: absolute;
  left: 50px;
  bottom: 50px;
}
.rules-wrapper {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(0, 0, 0, 0.65);
}
.rules {
  padding: 10px 50px;
  background: white;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.rules img {
  margin-top: 50px;
}
.close-rules {
  cursor: pointer;
  float: right;
  font-size: 30px;
  font-weight: bold;
}
@media (max-width: 550px) {
  .rules-button {
    bottom: 20px;
    left: 20px;
  }
  .rules {
    width: 100%;
    padding: 10px 10px

  }
  .rules img {
    margin-top: 20px;
    margin-bottom: 20px;
   width: 90%;
    margin-left: 5%;
  }
}
</style>
<template>
<div class="modal">
  <div class="modal-header">
    <h1>RULES</h1>
    <button @click="close" >X</button>
  </div>

</div>
</template>

<script>
export default {
  name: "RulesPopUp",
  props: {close},
}
</script>

<style scoped>
.modal {
  width: 60%;
  background: #fff;
  height: 500px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%,-50%);

}

</style>
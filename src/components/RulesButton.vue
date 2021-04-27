<template>

  <div class="button"></div>
  <RulesPopUp :close="closeModel" ></RulesPopUp>
</template>

<script>
import RulesPopUp from "@/components/RulesPopUp";
export default {
  name: "RulesButton",
  components: {
   RulesPopUp
  },
  methods: {
    closeModel() {
      console.log('works')
    }
  }
}
</script>

<style scoped>

</style>
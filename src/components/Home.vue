<template>
  <div>
    <h1>Trade or View your portfolio</h1>
    <h6>You may save & load your data</h6>
    <h6>Click on 'End day' to begin a new day!</h6>
    <hr />
    <p>Your funds: {{ funds }}</p>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import Header from "./Header.vue";
export default {
  components: {
    "app-header": Header
  },
  computed: {
    ...mapGetters({
      funds: "funds"
    })
  }
};
</script>

<style></style>

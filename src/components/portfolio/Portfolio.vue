<template>
  <div>
    <p>Funds: {{ funds | currency }}</p>
    <portfolio-stock v-for="stock in stocks" :stock="stock"></portfolio-stock>
  </div>
</template>

<script>
import Stock from "./Stock.vue";
import { mapGetters } from "vuex";
export default {
  computed: {
    ...mapGetters({
      stocks: "stockPortfolio",
      funds: "funds"
    })
  },
  components: {
    "portfolio-stock": Stock
  }
};
</script>

<style></style>

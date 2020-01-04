<template>
  <div class="container-fluid">
    <stock-card v-for="stock in stocks" :stock="stock" :key="stock.id">
    </stock-card>
  </div>
</template>

<script>
import Stock from "./Stock.vue";
export default {
  components: {
    "stock-card": Stock
  },
  computed: {
    stocks() {
      return this.$store.getters.stocks;
    }
  }
};
</script>

<style></style>

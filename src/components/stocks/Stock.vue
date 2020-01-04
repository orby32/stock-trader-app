<template>
  <div class="col-sm-6 col-md-4">
    <div class="panel panel-success">
      <div class="panel-heading">
        <h3 class="panel-title">
          {{ stock.name }}
          <small>Price: {{ stock.price | currency }}</small>
        </h3>
      </div>
      <div class="panel-body">
        <div class="pull-left">
          <input
            v-model="quantity"
            class="form-control"
            type="number"
            placeholder="Quantity"
            :class="{ danger: inSufficientFunds }"
          />
        </div>
        <div class="pull-right">
          <button
            class="btn btn-success"
            @click="buyStock"
            :disabled="quantity <= 0 || inSufficientFunds"
          >
            {{ inSufficientFunds ? "Insufficient funds" : "Buy" }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      quantity: 0
    };
  },
  computed: {
    funds() {
      return this.$store.getters.funds;
    },
    inSufficientFunds() {
      return this.funds < this.quantity * this.stock.price;
    }
  },
  props: ["stock"],
  methods: {
    buyStock() {
      const order = {
        stockId: this.stock.id,
        quantity: this.quantity,
        price: this.stock.price
      };
      this.$store.dispatch("buyStock", order);
      this.quantity = 0;
    }
  }
};
</script>

<style scoped>
.danger {
  border: 1px solid red;
}</style
>>

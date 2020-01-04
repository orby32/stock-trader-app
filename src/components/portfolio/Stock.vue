<template>
  <div class="col-sm-6 col-md-4">
    <div class="panel panel-info">
      <div class="panel-heading">
        <h3 class="panel-title">
          {{ stock.name }}
          <small
            >Price: {{ stock.price | currency }} | Quantity:
            {{ stock.quantity }}</small
          >
        </h3>
      </div>
      <div class="panel-body">
        <div class="pull-left">
          <input
            v-model="quantity"
            class="form-control"
            type="number"
            placeholder="Quantity"
          />
        </div>
        <div class="pull-right">
          <button
            class="btn btn-info"
            @click="sellStock"
            :disabled="quantity <= 0 || isEnoughQuantity"
            :class="{ danger: isEnoughQuantity }"
          >
            {{ isEnoughQuantity ? "Not enough stocks" : "Sell" }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex";
export default {
  data() {
    return {
      quantity: 0
    };
  },
  computed: {
    isEnoughQuantity() {
      return this.quantity > this.stock.quantity;
    }
  },
  props: ["stock"],
  methods: {
    ...mapActions({
      placeSellOrder: "sellStock"
    }),
    sellStock() {
      const order = {
        stockId: this.stock.id,
        quantity: this.quantity,
        price: this.stock.price
      };
      this.placeSellOrder(order);
      this.quantity = 0;
    }
  }
};
</script>

<style></style>

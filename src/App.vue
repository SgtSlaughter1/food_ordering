<template>
  <div id="app">
    <h1>Food Ordering App</h1>
    <DishList @add-to-cart="addToCart" @view-details="viewDetails" />
    <CartSummary :cart="cart" @remove-from-cart="removeFromCart" @reduce-quantity="reduceQuantity" />
    <OrderForm v-if="showForm" :is-disabled="isOrderDisabled" :name="name" :address="address"
      @confirm-order="openConfirmationModal" @update:name="name = $event" @update:address="address = $event" />
    <DishDetailModal v-if="selectedDish" :dish="selectedDish" @close="selectedDish = null" />
    <DishDetailModal v-if="showConfirmationModal" :dish="confirmationDetails" @close="closeConfirmationModal"
      :confirm="true" @confirm-order="placeOrder" />
    <p v-if="orderPlaced">Order Successful! Thank you for your purchase.</p>
  </div>
</template>

<script>
import DishList from "./components/DishList.vue";
import CartSummary from "./components/OrderSummary.vue";
import OrderForm from "./components/OrderForm.vue";
import DishDetailModal from "./components/DishModal.vue";

export default {
  components: {
    DishList,
    CartSummary,
    OrderForm,
    DishDetailModal,
  },
  data() {
    return {
      cart: [],
      selectedDish: null,
      showForm: true,
      showConfirmationModal: false,
      confirmationDetails: null,
      orderPlaced: false,
      name: "",
      address: "",
    };
  },
  computed: {
    isOrderDisabled() {
      return this.cart.length === 0 || !this.name || !this.address;
    },
  },
  methods: {
    addToCart(dish) {
      const cartItem = this.cart.find((item) => item.id === dish.id);
      if (cartItem) {
        cartItem.quantity++;
      } else {
        this.cart.push({ ...dish, quantity: 1 });
      }
    },
    viewDetails(dish) {
      this.selectedDish = dish;
    },
    removeFromCart(item) {
      this.cart = this.cart.filter((cartItem) => cartItem.id !== item.id);
    },
    reduceQuantity(item) {
      const cartItem = this.cart.find((cartItem) => cartItem.id === item.id);
      if (cartItem) {
        if (cartItem.quantity > 1) {
          cartItem.quantity--;
        } else {
          this.removeFromCart(item);
        }
      }
    },
    openConfirmationModal(details) {
      this.showConfirmationModal = true;
      this.confirmationDetails = {
        name: "Confirm Your Order",
        description: `Order for ${details.name}, 
        Address: ${details.address}.`,
      };
    },
    closeConfirmationModal() {
      this.showConfirmationModal = false;
      this.confirmationDetails = null;
    },
    placeOrder() {
      this.orderPlaced = true;
      this.showForm = false;
      this.cart = [];
      this.name = "";
      this.address = "";
    },
  },
};
</script>

<style>
#app {
  text-align: center;
}
</style>

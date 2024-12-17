<template>
    <div class="cart-summary">
        <h2>Cart Summary</h2>
        <ul>
            <li v-for="item in cart" :key="item.id">
                {{ item.name }} - Quantity: {{ item.quantity }} - Subtotal: ${{ (item.price * item.quantity).toFixed(2) }}
                <button class="remove" @click="$emit('remove-from-cart', item)">Remove</button>
                <button class="reduce" @click="$emit('reduce-quantity', item)">-</button>
            </li>
        </ul>
        <p><strong>Total Price: ${{ totalPrice.toFixed(2) }}</strong></p>
    </div>
</template>

<script>
export default {
    props: ['cart'],
    computed: {
        totalPrice() {
            return this.cart.reduce((sum, item) => sum + item.price * item.quantity, 0);
        },
    },
};
</script>

<style scoped>
.cart-summary {
    margin-top: 20px;
    text-align: center;
}
ul {
    list-style-type: none;
    padding: 0;
}
li {
    margin-bottom: 10px;
}
button {
    margin-left: 10px;
}
.remove {
    color: white;
    background: red;
    border-radius: 10px;
    padding: 5px;
    border: 1px solid white;
    cursor: pointer;
}
.reduce {
    background: orange;
    color: white;
    border-radius: 10px;
    padding: 5px;
    border: 1px solid white;
    cursor: pointer;
    width: 50px;
}
</style>


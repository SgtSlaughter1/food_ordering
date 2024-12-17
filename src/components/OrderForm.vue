<template>
    <form @submit.prevent="confirmOrder">
        <h3>Delivery Details</h3>
        <input v-model="formName" placeholder="Name" required @input="$emit('update:name', formName)" />
        <input v-model="formAddress" placeholder="Address" required @input="$emit('update:address', formAddress)" />
        <button type="submit" :disabled="isDisabled">Place Order</button>
    </form>
</template>

<script>
export default {
    props: ["isDisabled", "name", "address"],
    data() {
        return {
            formName: this.name,
            formAddress: this.address,
        };
    },
    watch: {
        name(newName) {
            this.formName = newName;
        },
        address(newAddress) {
            this.formAddress = newAddress;
        },
    },
    methods: {
        confirmOrder() {
            if (!this.isDisabled) {
                this.$emit("confirm-order", {
                    name: this.formName,
                    address: this.formAddress,
                });
            }
        },
    },
};
</script>

<style scoped>
form {
    display: flex;
    flex-direction: column;
    max-width: 300px;
    margin: 20px auto;
}

input {
    margin-bottom: 10px;
    padding: 5px;
}

button {
    background-color: #ff6347;
    color: #fff;
    border: 1px solid #fff;
    padding: 10px;
    cursor: pointer;
    border-radius: 15px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
}
</style>

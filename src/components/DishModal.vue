<template>
    <Teleport to="body">
        <div v-if="dish" class="modal-overlay" @click="$emit('close')">
            <div class="modal-content" @click.stop>
                <h2>{{ dish.name }}</h2>
                <p>{{ dish.description }}</p>
                <p v-if="dish.price">Price: ${{ dish.price }}</p>
                <button @click="$emit('close')">Cancel</button>
                <button v-if="confirm" @click="confirmOrder">Confirm Order</button>
            </div>
        </div>
    </Teleport>
</template>

<script>
    export default {
        props: ['dish', 'confirm'],
        methods: {
            confirmOrder() {
                this.$emit('confirm-order');
                this.$emit('close');
            },
        },
    };
</script>

<style scoped>
.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
}
.modal-content {
    background-color: #fff;
    padding: 20px;
    border-radius: 5px;
    text-align: center;
}
button {
    background: rgb(248, 85, 85);
    color: white;
    padding: 10px;
    border-radius: 10px;
    border: none;
    margin: 0 10px;
}
</style>

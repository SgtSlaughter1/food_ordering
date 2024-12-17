<template>
    <div class="dish-item">
        <img :src="dish.image" :alt="dish.name" />
        <h3>{{ dish.name }}</h3>
        <p>{{ dish.description }}</p>
        <p>${{ dish.price }}</p>
        <button class="view-details" @click="$emit('view-details', dish)">View Details</button>
        <button class="add-to-cart" @click="$emit('add-to-cart', dish)">Add to Cart</button>
    </div>
</template>

<script>
export default {
    props: ['dish'],
};
</script>

<style scoped>
.dish-item {
    border: 1px solid #ccc;
    padding: 15px;
    margin: 10px;
    width: 200px;
    text-align: center;
}
.dish-item > img {
    width: 200px;
    height: 200px;
    border-radius: 10px;
}
button {
    padding: 10px;
    margin: 5px;
    border: none;
    cursor: pointer;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}
.view-details {
    color: #ff6347;
    background: #fff;
    border: 1px solid #ff6347;
}
.add-to-cart {
    background-color: #ff6347;
        color: #fff;
        border: 1px solid #fff;
}
.add-to-cart:hover {
    background-color: #fff;
    color: black;
    border: 1px solid black;
}
</style>

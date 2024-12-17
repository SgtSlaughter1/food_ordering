<template>
    <div class="dish-list">
        <DishItem v-for="dish in dishes" :key="dish.id" :dish="dish" @add-to-cart="$emit('add-to-cart', dish)"
            @view-details="$emit('view-details', dish)" @reduce-quantity="$emit('reduce-quantity', dish)" />
    </div>
</template> 

<script>
import DishItem from './DishItem.vue';
export default {
    components: { DishItem },
    data() {
        return {
            dishes: [
                { id: 1, name: 'Spaghetti', price: 10, image: '/images/pasta.jpg', description: 'Delicious pasta with tomato sauce' },
                { id: 2, name: 'Pancake', price: 12, image: '/images/pancake.jpg', description: 'Cheesy pizza with pepperoni' },
                { id: 3, name: 'Pizza', price: 15, image: '/images/pizza.jpg', description: 'Cheesy pizza with pepperoni' },
                { id: 4, name: 'Fried Rice', price: 20, image: '/images/fried-rice.jpg', description: 'Cheesy pizza with pepperoni' },
            ],
        };
    },
};
</script>

<style scoped>
.dish-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}
</style>

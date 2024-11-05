<template>
    <div>
        <h2>Selecciona el teu producte</h2>
    
        <div v-for="(product, index) in products" :key="index">
            <span>{{ product.name }}  ${{ product.price }}</span>
            <button @click="addToCart(product)">Afegir a la cistella</button>
        </div>
    </div>

</template>

<script>
import { defineComponent, inject } from 'vue';

export default defineComponent({
    name: 'Order',
    setup(props, {emit}) {
        const products = [
            { name: 'Hamburguesa 🍔', price: 5.00 },
            { name: 'Cheeseburger 🧀', price: 6.00 },
            { name: 'Impossible Burger 🥕', price: 7.00 },
            { name: 'Patates 🍟', price: 2.00 }
        ];

        const addToCart = (product) => {
            emit('add-to-cart', product);
        }

        return{
            products, 
            addToCart
        };
    }
});
</script>
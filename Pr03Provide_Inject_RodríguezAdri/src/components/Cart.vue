<template>
    <div>
        <h2>Cistella de la comanda</h2>
        <p v-if="orderName"><strong>Nom de la comanda:</strong>{{ orderName }}</p>        
    
        <ul>
            <li v-for="(item, index) in cart" :key="index">
                {{ item.name }} - {{ item.price }}€
            </li>
        </ul>
    </div>
</template>

<script>
import { inject } from 'vue';

export default {
    name: 'Cart',
    setUp(){
        const orderName = inject('orderName');
        const cart = inject('cart');

        return {
            orderName,
            cart
        };
    }
};
</script>
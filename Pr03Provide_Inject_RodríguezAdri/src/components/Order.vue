<template>
    <div>
        <h1>HAMBURGUESERIA</h1>

        <input v-model="comandaName" placeholder="Introduïu el nom de la comanda" />
        <button @click="placeOrder"> Place Order </button>
        <button @click="changeDivisa"> Divisa</button>

        <Product :divisa="divisa" />
        <Cart :cart="cart" :divisa="divisa" :comandaName="comandaName" />
    </div>
</template>

<script setup>
    import { ref, provide } from 'vue';
    import Cart from './Cart.vue';
    import Product from './Product.vue';

    const comandaName = ref('');
    const cart = ref([]);
    const divisa = ref('EUR');

    const changeDivisa = () => {
        divisa.value = divisa.value === 'EUR' ? 'USD' : 'EUR';
    };


    const placeOrder = () => {
        if (cart.value.length > 0 || comandaName.value) {
            alert(`Comanda de: ${comandaName.value}`);
            comandaName.value = '';
            cart.value = [];
        } else {
            alert('Comanda buida!')
        }
    };


    const addToCart = (product) => {
        if (!comandaName.value) {
        alert('Es necessita introduir el nom de la comanda abans d\'afegir productes.');
      return;
    }
        cart.value.push(product);
    }

    provide('Afegir a la cistella', addToCart);
    provide('divisa', divisa);
</script>
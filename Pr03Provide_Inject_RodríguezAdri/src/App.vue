<template>
  <div>
    <h1>HAMBURGUESERIA</h1>

    <input v-model="orderName" placeholder="Nom de la comanda">

    <button @click="showNameOrder">Place Order</button>

    <Order @add-to-cart="addToCart"/>
    <Cart/>
  </div>
</template>

<script >
import Order from './components/Order.vue';
import Cart from './components/Cart.vue';
import { ref, provide } from 'vue';

export default {
  name: 'App',
  components: {
    Order,
    Cart
  },
  setup() {
    const orderName = ref("");
    const showName= ref(false);
    const cart = ref([]);

    const showNameOrder = () => {
      // showName.value = !showName.value
    };

    const addToCart = (product) => {
      cart.value.push(product);
      alert(`Comanda actual: ${cart.value.map(item => item.name).join(', ')}`);
    };


    provide('orderName', orderName);
    provide('cart', cart);


    return{
      orderName,
      cart,
      showNameOrder,
      addToCart
    };
  }
};

</script>



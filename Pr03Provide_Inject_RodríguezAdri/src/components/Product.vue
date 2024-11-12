<template>
  <div>
    <h2>PRODUCTES</h2>

    <ul>
      <li v-for="product in products" :key="product.name">
        <p>{{ product.name }} - {{ product.price }}</p>
        <button @click="addToCart(product)">Add</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { inject, defineProps} from 'vue'

// Definir las props
const props = defineProps({
  divisa: {
    type: String,
    required: true,
  }
});

const products = [
  { name: "Hamburger 🍔", price: 5.00 },
  { name: "Cheeseburger 🧀", price: 6.00 },
  { name: "Impossible Burger 🥕", price: 7.00 },
  { name: "Fries 🍟", price: 2 },
];

const addToCart = inject('Afegir a la cistella');

</script>

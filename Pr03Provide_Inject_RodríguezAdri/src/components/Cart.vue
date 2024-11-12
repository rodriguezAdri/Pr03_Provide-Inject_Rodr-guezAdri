<template>
    <div>
      <h2>CISTELLA: {{ comandaName }}</h2>
      <ul>
        <li v-for="product in cart" :key="product.name">
          <p>{{ product.name }} - {{ getPrice(product.price) }} - {{ divisa }}</p>
        </li>
      </ul>
    </div>
  </template>
  
  <script setup>
  import { defineProps } from 'vue'
  
  // Definir las props
  const props = defineProps({
    cart: {
        type: Array,
        required: true
    },
    divisa: {
        type: String,
        required: true
    },
    comandaName:{
        type: String,
        required: true
    }
  });

  const getPrice = (price) => {
  return props.divisa === 'EUR' ? `${price}€` : `${(price * 0.93).toFixed(2)}$`;
}
  </script>
  
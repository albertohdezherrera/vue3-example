
<template>
  <table>
    <tr>
      <th>id</th>
      <th>name</th>
    </tr>
    <tr v-for="product in state.products" :key="product.id">
      <td>{{ product.id }}</td>
      <td>{{ product.name }}</td>
    </tr>
  </table>
  <button @click="orderItems(state.products)">Ordenar ({{ orderState.direction }})</button>
</template>

<script>

import { reactive } from 'vue';
import order from '../services/order-manual.js';

export default {
  name: 'ProductTable',
  setup() {
    const state = reactive({
      products: [
        { id: 0, name: 'Mesa'},
        { id: 1, name: 'Silla' },
        { id: 2, name: 'Lápiz'},
        { id: 3, name: 'Portatil'},
      ]
    });

    const { orderItems, orderState } = order();

    return {
      state,
      orderItems,
      orderState
    };
  }
}
</script>
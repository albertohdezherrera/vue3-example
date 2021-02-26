<template>
  <h2>{{ text }} - {{ upperCase }}</h2>
  <table>
    <tr>
      <th>id</th>
      <th>name</th>
    </tr>
    <tr v-for="user in state.users" :key="user.id">
      <td>{{ user.id }}</td>
      <td>{{ user.name }}</td>
    </tr>
  </table>
  <button @click="orderItems(state.users)">Ordenar ({{ orderState.direction }})</button>
</template>

<script>
import { reactive, ref, computed } from 'vue';
import order from '../services/order-manual.js';

export default {
  name: 'UserTable',
  setup() {
    const text = ref('Empleados ECI');
    const state = reactive({
      users: [
        { id: 0, name: 'Soleto' },
        { id: 1, name: 'Carlos' },
        { id: 2, name: 'Oscar' },
        { id: 3, name: 'Francisco' },
        { id: 4, name: 'Alberto' },
      ]
    });
    
    const { orderItems, orderState } = order();

    const upperCase = computed(() => {
      console.log(text.value);
      return text.value.toUpperCase();
    });

    return {
      state,
      orderItems,
      orderState,
      text,
      upperCase
    };
  }
}
</script>
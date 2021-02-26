<template>
  <div>
    <Classic />
    <hr>
    <Suspense>
      <template #default>
        <SuspenseHeader name="a todos" />
      </template>
      <template #fallback>
        <h1>Cargando componente....</h1>
      </template>
    </Suspense>
    <hr>
    <ProductTable />
    <hr>
    <UserTable />
    <hr>
    <div>
      <h2>Contador</h2>
      <h3>{{ clicks }}</h3>
      {{ count }}
      <button @click="increaseCount()">Incrementar</button>
      <button @click="double()">Doble</button>
    </div>
  </div>
</template>

<script>
import { ref, computed } from 'vue';
import ProductTable from './components/ProductTable';
import UserTable from './components/UserTable';
import SuspenseHeader from './components/SuspenseHeader';
import Classic from './components/Classic'

export default {
  name: 'App',
  components: {
    ProductTable,
    UserTable,
    SuspenseHeader,
    Classic
  },
  setup() {
    const count = ref(0);
    const countClick = ref(0);

    function increaseCount() {
      countClick.value++;
      count.value++;
    }

    const double = () => {
      count.value *= 2;
    };

    const clicks = computed(() => `Has aumentado ${countClick.value} veces`);

    return {
      count,
      increaseCount,
      double,
      countClick,
      clicks
    }
  }
}
</script>

<style>
  body {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
    margin: 0;
    padding: 1rem;
  }
  table {
    border: 0;
  }
  th {
    border: 0;
    padding: 4px 0;
  }
  td {
    border: 0;
    padding: 4px;
  }
  button {
    border: 1px solid #999;
    padding: 4px;
    font-size: 0.9rem;
    margin-top: 10px;
    margin-bottom: 10px;
  }
  button:hover {
    cursor: pointer;
    background: rgb(102, 138, 221);
  }
  h1 {
    margin: 0;
  }
</style>
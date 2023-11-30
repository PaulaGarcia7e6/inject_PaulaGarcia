<template>
  <header>
    <h1>{{ nombreComanda }}</h1>
    <input type="text" name="" id="" v-model="nombreComanda">
    <input type="submit" value="Place Order" id="placeOrder">
  </header>

  <main>
    <label for="currency">Currency</label>
    <select name="currency" id="currency">
      <option value="$">Dollars($)</option>
      <option value="€">Euros(€)</option>
    </select>
    <comanda v-for="producto of productes" key="" :producte="producto" />
  </main>
</template>

<script setup lang="ts">
import { reactive, ref, type Ref } from 'vue';
import comanda from './components/comanda.vue';
import type { Producto } from './type/Producto';

const productes: Array<Producto> = reactive([
  { name: "Hamburger 🍔.", price: 5 },
  { name: "Cheeseburger 🧀", price: 6 },
  { name: "Impossible Burger 🥕", price: 7 },
  { name: "Fries 🍟", price: 2 }
])

const nombreComanda: Ref<string> = ref('The Snazzy Burger')
</script>

<style scoped></style>

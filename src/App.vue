<template>
  <header>
    <h1>{{ nombreComanda }}</h1>
    <input type="text" name="" id="" v-model="nombreComanda">
    <input type="submit" value="Place Order" id="placeOrder" @click="placeOrder()">
  </header>

  <main>
    <label for="currency">Currency</label>
    <select name="currency" v-model="currency">
      <option value="$">Dollars($)</option>
      <option value="€">Euros(€)</option>
    </select>
    <ul class="c-comanda">
      <comanda v-for="producto of productes" key="" :producte="producto" @nom-producte="recibirHijo" />
    </ul>
  </main>
</template>

<script setup lang="ts">
import { provide, reactive, ref, watch, type Ref } from 'vue';
import comanda from './components/comanda.vue';
import type { Producto } from './type/Producto';

const arrayComanda: Array<string> = reactive([])
const productes: Array<Producto> = reactive([
  { name: "Hamburger 🍔", price: 5 },
  { name: "Cheeseburger 🧀", price: 6 },
  { name: "Impossible Burger 🥕", price: 7 },
  { name: "Fries 🍟", price: 2 }
])

const currency: Ref<string> = ref('€')
const nombreComanda: Ref<string> = ref('The Snazzy Burger')
provide('moneda', currency)
// watch(currency, () => {
//   provide('moneda', currency.value)d
// })
const recibirHijo = (data: string) => {
  // Manejar los datos emitidos por el componente hijo
  //console.log(data)
  arrayComanda.push(data);
  alert(arrayComanda)
}
function placeOrder() {
  alert('Your order has been placed!')
}
</script>

<style scoped></style>

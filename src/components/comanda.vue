<template>
    <li>
        <p>
            {{ props.producte.name }} <price :precio="props.producte.price"/>
        </p>
        <button @click="addcomand(props.producte.name)">Add to Cart</button>
    </li>
</template>
<script setup lang="ts">
import price from './price.vue';
import type { Producto } from '../type/Producto';
import { defineEmits } from 'vue';

const props = defineProps<{
    producte: Producto,
}>()
const emitPadre = defineEmits<{
  (e: 'nomProducte', value: string): void
}>()
function addcomand(producte:string) {
    emitPadre('nomProducte',props.producte.name)
}

</script>
<style scoped>
li {
    list-style: none;
    display: flex;
}
</style>
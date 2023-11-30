<template>
{{ props.producte.name }} <price/>
</template>
<script setup lang="ts">
import price from './price.vue';
import type { Producto } from '../type/Producto';

const props = defineProps<{
    producte: Producto,
}>()
</script>
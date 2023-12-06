<template>
{{ precioConvertido }} {{ moneda }}
</template>
<script setup lang="ts">
import { inject, ref, watch } from 'vue';
const props = defineProps({
  precio:Number,
});
const moneda= ref<string>(inject<string>('moneda',''))
let precioConvertido = props.precio

watch(moneda, () => {
  console.log(moneda.value)
  if (moneda.value == '$') {
    precioConvertido = convertirEuroADolar(precioConvertido as number)
  } else {
    precioConvertido = props.precio
  }
})

function convertirEuroADolar(cantidadEuro: number): number {
  const tasaConversion = 1.08;
  const cantidadDolar = cantidadEuro * tasaConversion;
  return cantidadDolar;
}

</script>
<template>
{{ moneda }}
</template>
<script setup lang="ts">
import { inject, ref, type Ref } from 'vue';
const props = defineProps({
  precio:Number,
});
const emitComanda = defineEmits(['nomProducte'])
const moneda= inject<string>('moneda')
console.log(moneda)

</script>
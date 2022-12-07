<script setup>
import {ref, watch, defineEmits} from 'vue'
import { useItemComparison } from '../composables/itemComparison'

const selected = ref();
const data = ref();
const emit = defineEmits(['select'])

fetch('https://dummyjson.com/products')
    .then(res => res.json())
    .then(res => {
      data.value = res.products;
    });

watch(() => selected.value, (value) => {
  emit('select', value);
})
</script>

<template>
  <select v-model="selected" class="p-2 border-2 border-gray-dark">
    <option disabled value="">Select an item</option>
    <option v-for="item in data" :value="item">{{`${item.title} - $${item.price}`}}</option>
  </select>
</template>

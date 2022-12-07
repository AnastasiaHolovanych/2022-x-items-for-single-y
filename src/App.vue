<script setup>
import {ref} from 'vue'
import ItemSelect from './components/ItemSelect.vue'
import ComparisonSummary from './components/ComparisonSummary.vue'

const selectFirst = ref()
const selectSecond = ref()
const onSelectFirst = (data) => {
  selectFirst.value = data
}
const onSelectSecond = (data) => {
  selectSecond.value = data
}
</script>

<template>
  <div class="w-full h-full flex flex-col gap-5 justify-center items-center">
    <h1 class="text-4xl font-bold">Select items to compare</h1>
    <div class="flex flex-col gap-5 justify-center">
      <ItemSelect @select="onSelectFirst" />
      <ItemSelect @select="onSelectSecond"/>
    </div>
    <ComparisonSummary :selectFirst="selectFirst" :selectSecond="selectSecond"/>
  </div>
</template>

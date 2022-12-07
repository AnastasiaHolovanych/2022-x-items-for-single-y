<template>
  <p v-if="!theSame" class="mx-5 text-center">
    You can get <strong>{{n}}x</strong> <em>{{selectFirst.title || ''}} items</em> for about the same price as a single <em>{{selectSecond.title || ''}} item</em>
  </p>
  <p v-else class="mx-5 text-center">
    These are the same items message
  </p>
</template>

<script setup>
import {computed, ref} from "vue";

const props = defineProps({
  selectFirst: {},
  selectSecond: {},
})
const theSame = ref(false)

const n = computed(() => {
  if (props.selectFirst && props.selectSecond) {
    if (props.selectFirst.id !== props.selectSecond.id) {
      theSame.value = false
      return Math.floor(props.selectFirst.price / props.selectSecond.price)
    }
    theSame.value = true;
  }
  return ''
})
</script>

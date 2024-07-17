<template>
  <img :src="src" :alt="alt" class="payment-method" />
</template>

<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  src: {
    type: String,
    required: true
  },
  alt: {
    type: String,
    required: true
  }
})
</script>

<style scoped>
.payment-method {
  margin: 5px;
  width: 50px;
  height: auto;
}
</style>


<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  label: String,
  value: String,
  valueClass: {
    type: String,
    default: ''
  }
})
</script>

<template>
  <div class="detail-item">
    <span class="detail-item__label">{{ label }}: </span>
    <span :class="['detail-item__value', `detail-item__value--${valueClass}`]">{{ value }}</span>
  </div>
</template>

<style scoped>
.detail-item {
  font-family: Arial, sans-serif;
  margin-bottom: 5px;
}

.detail-item__label {
  color: #666;
}

.detail-item__value {
  color: #000;
}

.detail-item__value--orange {
  color: #e66000;
}
</style>

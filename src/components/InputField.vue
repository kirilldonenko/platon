<script setup>
defineProps({
  modelValue: String,
  placeholder: String,
});
</script>

<template>
  <input class="form__control" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)" :placeholder="placeholder" />
</template>

<style scoped>
.form__control {
  width: 100%;
  position: relative;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
  padding: 12px 25px 12px 10px;
  outline: none;
  font-size: 16px;
  font-family: "Roboto", sans-serif;
  background-color: #f2f2f2;
  border: 1px solid transparent;
  text-align: center;
  appearance: none;
}
.form__control:hover {
  border-color: #777777;
}
</style>

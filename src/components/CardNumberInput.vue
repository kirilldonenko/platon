<script setup>
import { ref, watch, defineProps, defineEmits } from 'vue';

const props = defineProps({
  modelValue: String,
  placeholder: String,
});

const emit = defineEmits(['update:modelValue']);

const formattedValue = ref('');
const inputValue = ref('');
const isInvalid = ref(false);
const errorMessage = ref('');

// Define functions first before using them in setup
const formatCardNumber = (value) => {
  let result = '';
  for (let i = 0; i < 16; i++) {
    if (i < value.length) {
      result += value[i];
    } else {
      result += 'x';
    }
    if ((i + 1) % 4 === 0 && i < 15) {
      result += ' ';
    }
  }
  return result;
};

const validateCardNumber = (value) => {
  if (value.length !== 16) {
    errorMessage.value = 'Card number must be 16 digits long.';
    isInvalid.value = true;
  } else {
    errorMessage.value = '';
    isInvalid.value = false;
  }
};

watch(() => props.modelValue, (newVal) => {
  inputValue.value = newVal || '';
  formattedValue.value = formatCardNumber(inputValue.value);
  validateCardNumber(inputValue.value);
}, { immediate: true });

const onInput = (event) => {
  const rawValue = event.target.value.replace(/\D/g, '');
  if (rawValue !== event.target.value.replace(/ /g, '')) {
    errorMessage.value = 'Card number must contain only digits.';
    isInvalid.value = true;
  } else {
    inputValue.value = rawValue;
    formattedValue.value = formatCardNumber(rawValue);
    emit('update:modelValue', rawValue);
    validateCardNumber(rawValue);
  }
};
</script>

<template>
  <div>
    <input
        class="form__control"
        :class="{'is-invalid': isInvalid}"
        :value="formattedValue"
        @input="onInput"
        :placeholder="placeholder"
        inputmode="numeric"
        name="cc-number"
        autocomplete="cc-number"
        type="text"
    />
    <div v-if="isInvalid" class="error-message">{{ errorMessage }}</div>
  </div>
</template>

<style scoped>
.form__control {
  width: 100%;
  position: relative;
  align-items: center;
  justify-content: center;
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
.error-message {
  color: red;
  margin-top: 4px;
}
</style>

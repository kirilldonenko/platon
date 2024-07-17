<script setup>
import { ref, watch } from 'vue';

const cardNumber = ref(null);
const month = ref(null);
const year = ref(null);
const cvv = ref(null);
const submit = () => {
  console.log('Card Number:', cardNumber.value);
  console.log('Month:', month.value);
  console.log('Year:', year.value);
  console.log('CVV:', cvv.value);
}

const props = defineProps({
  modelValue: String,
  placeholder: String,
});

const emit = defineEmits(['update:modelValue']);

const formattedValue = ref('');
const inputValue = ref('');
const isInvalid = ref(false);
const errorMessage = ref('');

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
  <form class="payment-form" @submit.prevent="submit">
    <div class="payment-form__row">
      <input
          class="payment-form__control"
          :class="{'is-invalid': isInvalid}"
          :value="formattedValue"
          @input="onInput"
          placeholder="xxxx xxxx xxxx xxxx"
          inputmode="numeric"
          name="cc-number"
          autocomplete="cc-number"
          type="text"
      />
      <div v-if="isInvalid" class="error-message">{{ errorMessage }}</div>
    </div>
    <div class="payment-form__row-multi">
      <input class="payment-form__control" v-model="month" placeholder="MM" />
      <input class="payment-form__control" v-model="year" placeholder="YY" />
      <input class="payment-form__control" v-model="cvv" placeholder="CVV2/CVC2" />
    </div>
    <label>
      <input type="checkbox" />
      Guarantee of fast return of funds
    </label>
    <a href="#">(public policy)</a>
    <button type="submit">PAY</button>
  </form>
</template>

<style scoped>
.payment-form {
  width: 100%;
  max-width: 596px;
  padding: 10px;
  border-radius: 15px;
  background-color: #fff;
  box-shadow: 0 12px 29px rgba(0, 0, 0, 0.12);
}
.payment-form__row {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: stretch;
}
.payment-form__row-multi {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  flex-wrap: wrap;
}
.payment-form__row-multi .payment-form__control {
  max-width: 48%;
}
.payment-form__control {
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
.payment-form__control:hover {
  border-color: #777777;
}
.error-message {
  color: red;
  margin-top: 4px;
}
@media only screen and (min-width: 950px) {
  .payment-form {
    max-width: 425px;
    padding: 40px;
  }
}
</style>

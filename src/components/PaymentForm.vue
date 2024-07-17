<script setup>
import { ref } from "vue";
import CardNumberInput from "@/components/CardNumberInput.vue";
import InputField from "@/components/InputField.vue";

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
</script>

<template>
  <form class="form" @submit.prevent="submit">
    <CardNumberInput v-model="cardNumber" placeholder="xxxx xxxx xxxx xxxx" />
    <InputField v-model="month" placeholder="MM" />
    <InputField v-model="year" placeholder="YY" />
    <InputField v-model="cvv" placeholder="CVV2/CVC2" />
    <label>
      <input type="checkbox" />
      Guarantee of fast return of funds
    </label>
    <a href="#">(public policy)</a>
    <button type="submit">PAY</button>
  </form>
</template>

<style scoped>
.form {
  padding: 10px;
  border-radius: 15px;
  background-color: #fff;
  box-shadow: 0 12px 29px rgba(0, 0, 0, 0.12);
}
</style>

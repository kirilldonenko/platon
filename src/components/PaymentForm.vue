<script setup>
import { nextTick, onMounted, ref, watch } from 'vue';
import Warning from '@/assets/images/warning.svg'
import Inputmask from 'inputmask';

const cardNumber = ref('');
const month = ref('');
const year = ref('');
const cvv = ref('');
const formattedCardNumber = ref('xxxx xxxx xxxx xxxx');
const isCardNumberInvalid = ref(false);
const isMonthInvalid = ref(false);
const isYearInvalid = ref(false);
const isCvvInvalid = ref(false);
const inputRef = ref(null);
const submit = () => {
  console.log('Card Number:', cardNumber.value);
  console.log('Month:', month.value);
  console.log('Year:', year.value);
  console.log('CVV:', cvv.value);
}

const updateCardNumber = (event) => {
  const value = event.target.value;
  formattedCardNumber.value = value;
  cardNumber.value = value.replace(/\s/g, '');
}

const validateCardNumber = () => {
  isCardNumberInvalid.value = cardNumber.value.replace(/x/g, '').length !== 16;
};
const validateMonth = (value) => {
  if (value < 1 || value > 12 || value?.length !== 2) {
    isMonthInvalid.value = true;
  } else {
    isMonthInvalid.value = false;
  }
};

const validateYear = (value) => {
  if (value < 24 || value?.length !== 2) {
    isYearInvalid.value = true;
  } else {
    isYearInvalid.value = false;
  }
};

const validateCvv = (value) => {
  if (value?.length !== 3) {
    isCvvInvalid.value = true;
  } else {
    isCvvInvalid.value = false;
  }
};

const onMonthInput = (event) => {
  let value = event.target.value.replace(/\D/g, '');

  if (value.length > 2) {
    month.value = value.slice(0, 2);
    return;
  }
  if (value > 12) {
    value = '12';
  } else if (value <= 0 && value.length === 2) {
    value = '01';
  } else if (value > 0 && value < 10) {
    value = value.padStart(2, 0)
  }

  month.value = value;
};
const onMonthBlur = () => {
  validateMonth(month.value);
};

const onYearInput = (event) => {
  let value = event.target.value?.replace(/\D/g, '') || '';
  if (value < 24 && value?.length === 2) {
    value = '24';
  }
  if (value.length > 2) {
    year.value = value.slice(0, 2);
    return;
  }
  year.value = value;
};
const onYearBlur = () => {
  validateYear(year.value);
};
const onCvvInput = (event) => {
  const value = event.target.value.replace(/\D/g, '');
  cvv.value = value.slice(0, 3);
};
const onCvvBlur = () => {
  validateCvv(cvv.value);
};
const onBlurCardNumber = () => {
  validateCardNumber();
};

onMounted(() => {
  nextTick(() => {
    const inputmask = new Inputmask({
      mask: '9999 9999 9999 9999',
      placeholder: 'x',
      oncomplete: () => {
        cardNumber.value = formattedCardNumber.value.replace(/\s/g, '');
      },
      onincomplete: () => {
        cardNumber.value = formattedCardNumber.value.replace(/\s/g, '');
      },
    });
    inputmask.mask(inputRef.value);
  });
});
</script>

<template>
  <div class="payment-form">
    <div v-if="isCardNumberInvalid || isMonthInvalid || isYearInvalid || isCvvInvalid" class="warning">
      <div class="warning__icon">
        <img :src="Warning" alt="Warning">
      </div>
      <div class="warning__body">
        <div class="warning__title">Error</div>
        <div v-if="isCardNumberInvalid" class="warning__text">Card number: invalid card number</div>
        <div v-if="isMonthInvalid" class="warning__text">Validity: month are incorrect</div>
        <div v-if="isYearInvalid" class="warning__text">Validity: year are incorrect</div>
        <div v-if="isCvvInvalid" class="warning__text">CVV2/CVC2: CVV2/CVC2 are incorrect</div>
      </div>
    </div>
    <form class="payment-form__form" @submit.prevent="submit">
      <div class="payment-form__row-first">
        <div class="payment-form__item">
          <input
              class="payment-form__control"
              v-model="formattedCardNumber"
              @input="updateCardNumber"
              placeholder="xxxx xxxx xxxx xxxx"
              ref="inputRef"
              @blur="onBlurCardNumber"
              inputmode="numeric"
              name="cc-number"
              autocomplete="cc-number"
              type="text"
          />
          <div class="payment-form__icon" title="Enter the card number (16 digits)">
            <svg width="19" height="19" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
              <path d="M13.17,16.8h1.42v1.52H9.39V16.8H10.8V10.69H9.39V9.17h3.78ZM13.09,5.44V7.63H10.51V5.44Z"></path>
            </svg>
          </div>
          <div v-if="formattedValue" class="payment-form__clear"></div>
        </div>
      </div>
      <div class="payment-form__row">
        <div class="payment-form__row-multi">
          <div class="payment-form__item">
            <input
                class="payment-form__control"
                v-model="month"
                @input="onMonthInput"
                @blur="onMonthBlur"
                placeholder="MM"
                inputmode="numeric"
                name="cc-number"
                autocomplete="cc-number"
                type="number"
            />
            <div class="payment-form__icon" title="Indicate the validity period of your card (month)">
              <svg width="19" height="19" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path d="M13.17,16.8h1.42v1.52H9.39V16.8H10.8V10.69H9.39V9.17h3.78ZM13.09,5.44V7.63H10.51V5.44Z"></path>
              </svg>
            </div>
          </div>
          <div class="payment-form__item">
            <input
                class="payment-form__control"
                v-model="year"
                @input="onYearInput"
                @blur="onYearBlur"
                placeholder="YY"
                inputmode="numeric"
                name="cc-number"
                autocomplete="cc-number"
                type="number"
            />
            <div class="payment-form__icon" title="Enter the year">
              <svg width="19" height="19" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path d="M13.17,16.8h1.42v1.52H9.39V16.8H10.8V10.69H9.39V9.17h3.78ZM13.09,5.44V7.63H10.51V5.44Z"></path>
              </svg>
            </div>
          </div>
        </div>
        <div class="payment-form__row-last">
          <div class="payment-form__item">
            <input
                class="payment-form__control"
                v-model="cvv"
                @input="onCvvInput"
                @blur="onCvvBlur"
                type="password"
                placeholder="CVV2/CVC2"
                inputmode="numeric"
                name="cc-number"
                autocomplete="cc-number"
            />
            <div class="payment-form__icon" title="The last 3 digits on the back of your card">
              <svg width="19" height="19" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path d="M13.17,16.8h1.42v1.52H9.39V16.8H10.8V10.69H9.39V9.17h3.78ZM13.09,5.44V7.63H10.51V5.44Z"></path>
              </svg>
            </div>
          </div>
        </div>
      </div>
      <label>
        <input type="checkbox" />
        Guarantee of fast return of funds
      </label>
      <a href="https://platon.ua/policy.pdf" target="_blank">(public policy)</a>
      <div class="payment-form__button-row">
        <button class="payment-form__button" type="submit" @click.prevent="submit">PAY</button>
      </div>
    </form>
  </div>
</template>

<style scoped>
.payment-form {
  position: relative;
  margin-bottom: 30px;
  padding: 60px 42px 0;
}

.payment-form__form {
  padding: 40px;
  border-radius: 15px;
  background-color: #fff;
  box-shadow: 0 12px 29px rgba(0, 0, 0, 0.12);
  width: 100%;
  min-width: 320px;
  max-width: 425px;
  box-sizing: border-box;
}
.payment-form__row-first {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: stretch;
  margin-bottom: 20px;
}
.payment-form__row {
  display: flex;
  justify-content: stretch;
  align-items: center;
  flex-wrap: wrap;
}
.payment-form__row-multi {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.payment-form__row-multi .payment-form__item {
  max-width: 48%;
  margin-bottom: 20px;
}
.payment-form__row-last {
  width: 100%;
  margin-bottom: 35px;
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
  width: 100%;
  box-sizing: border-box;
}
.warning {
  position: absolute;
  top: 3px;
  left: 0;
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  padding: 8px 15px 12px;
  margin-bottom: 15px;
  width: 100%;
  background-color: #fef2f3;
  line-height: 1;
}
.payment-form__control:hover {
  border-color: #777777;
}
.payment-form__control:focus {
  border-color: #ff0000;
}
.payment-form__item {
  position: relative;
}
.payment-form__icon {
  position: absolute;
  right: 0;
  top: 50%;
  width: 24px;
  height: 24px;
  margin-top: -19px;
  z-index: 2;
  cursor: pointer;
  fill: #777;
  transition: 0.2s ease;
  opacity: unset !important;
}
.payment-form__clear {
  position: absolute;
  right: 10px;
  top: 50%;
  width: 10px;
  height: 10px;
  margin-top: -5px;
  z-index: 2;
  cursor: pointer;
  background: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16.41 16.41'><polygon points='16.41 1.41 15 0 8.21 6.79 1.41 0 0 1.41 6.79 8.21 0 15 1.41 16.41 8.21 9.62 15 16.41 16.41 15 9.62 8.21 16.41 1.41' fill='rgba(235, 0, 27)'/></svg>") no-repeat center center;
  background-size: 20px 20px;
  display: none;
}
.payment-form__button-row {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}
.payment-form__button {
  font-family: "Roboto", sans-serif;
  font-size: 18px;
  height: 45px;
  border-radius: 25px;
  padding: 0 45px;
  outline: none;
  border: none;
  background: linear-gradient(to right, #373737 0%, #000000 100%);
  color: #fff;
  cursor: pointer;
}
.warning__icon {
  margin-right: 20px;
}
.warning__title, .warning__text {
  margin-bottom: 3px;
  text-align: left;
  color: #eb001b;
}
.warning__text {
  font-size: 12px;
}
@media only screen and (min-width: 950px) {
  .payment-form__form {
    max-width: 425px;
  }
}
</style>

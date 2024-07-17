<script setup>
import UA from '@/assets/ua.svg'
import EN from '@/assets/en.svg'
</script>

<template>
  <div class="payment-details__lang-switcher">
    <img :src="UA" width="24" height="24" alt="UA">
    <img :src="EN" width="24" height="24" alt="EN">
  </div>
</template>

<style scoped>
@media only screen and (max-width: 768px) {
  .payment-details__lang-switcher::after {
    content: '';
    background: url(@/assets/arrow.svg) no-repeat right center;
    position: absolute;
    width: 24px;
    height: 12px;
    right: 0;
    top: 7px;
  }
}
</style>

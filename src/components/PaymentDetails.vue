<script setup>

import DetailsHeader from "@/components/DetailsHeader.vue";
import DetailsInfo from "@/components/DetailsInfo.vue";
import PaymentCards from "@/components/PaymentCards.vue";
</script>

<template>
  <div class="payment-details">
    <DetailsHeader />
    <DetailsInfo />
    <PaymentCards />
  </div>
</template>

<style scoped>
.payment-details {
  position: relative;
  width: 100%;
  max-width: 680px;
  box-shadow: 0 23px 79px rgba(0, 0, 0, 0.16);
  z-index: 2;
  background: #fff;
}
@media only screen and (min-width: 950px) {
  .payment-details {
    width: 360px;
  }
}
</style>

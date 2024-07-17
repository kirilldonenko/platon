<script setup>
import Logo from '@/assets/images/logo.svg'
import LangsSwitcher from "@/components/LangsSwitcher.vue";
</script>

<template>
<div class="details-header">
  <LangsSwitcher />
  <img :src="Logo" width="180" height="auto">
</div>
</template>

<style scoped>
.details-header {
  display: flex;
  flex-direction: row-reverse;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 30px;
  padding: 15px 15px 0;
}
@media only screen and (min-width: 435px) {
  .details-header {
    border-bottom: none;
    padding: 35px 25px 0 38px;
  }
}
</style>
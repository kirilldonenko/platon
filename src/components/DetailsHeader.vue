<script setup>
import Logo from '@/assets/images/logo.svg'
import LangsSwitcher from "@/components/LangsSwitcher.vue";
</script>

<template>
<div class="details-header">
  <LangsSwitcher class="details-header__switcher" />
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
@media only screen and (min-width: 950px) {
  .details-header {
    flex-direction: column;
    align-items: flex-start;
    padding-bottom: 22px;
    border-bottom: 1px solid #e5e5e5;
  }
  .details-header__switcher {
    align-self: end;
  }
}
</style>

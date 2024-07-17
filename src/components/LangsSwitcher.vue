<script setup>
import EN from '@/assets/images/en.svg'
import UA from '@/assets/images/ua.svg'
</script>

<template>
<div class="lang-switcher">
  <img class="lang-switcher__lang lang-switcher__lang--in-active" :src="UA" alt="UA"/>
  <img class="lang-switcher__lang" :src="EN" alt="EN" />
</div>
</template>

<style scoped>
.lang-switcher {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
}
.lang-switcher__lang {
  margin-right: 30px;
}
@media only screen and (max-width: 768px) {
  .lang-switcher {
    flex-direction: row;
  }
  .lang-switcher:after {
    content: '';
    background: url('../assets/images/arrow.svg') no-repeat right center;
    position: absolute;
    width: 24px;
    height: 12px;
    right: 0;
    top: 7px;
  }
  .lang-switcher__lang--in-active {
    display: none;
  }
}
@media only screen and (min-width: 768px) {
  .lang-switcher {
    flex-direction: row;
  }
}
</style>

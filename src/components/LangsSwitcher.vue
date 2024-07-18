<script setup>
import EN from '@/assets/images/en.svg'
import UA from '@/assets/images/ua.svg'
</script>

<template>
<div class="lang-switcher">
  <img class="lang-switcher__lang" :src="UA" alt="UA"/>
  <img class="lang-switcher__lang lang-switcher__lang--active" :src="EN" alt="EN" />
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
.lang-switcher__lang:hover, .lang-switcher__lang--active {
  border-radius: 50%;
  box-shadow: 0 0 0 2px #fff, 0 0 0 3px #e66000;
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
.lang-switcher__lang {
  display: none;
}
.lang-switcher__lang--active {
  display: block;
}
@media only screen and (min-width: 768px) {
  .lang-switcher {
    flex-direction: row;
  }
}
@media only screen and (min-width: 950px) {
  .lang-switcher {
    flex-direction: row;
  }
  .lang-switcher__lang {
    margin-right: 10px;
  }
  .lang-switcher__lang {
    display: block;
  }
  .lang-switcher:after {
    display: none;
  }
}
</style>

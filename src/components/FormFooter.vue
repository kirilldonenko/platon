<script setup>
import Logo from '@/assets/images/logo.svg'
import Master from '@/assets/images/master.png'
import VerifyVisa from '@/assets/images/verify-visa.png'
import MasterCardSecure from '@/assets/images/master-card.png'
import PCI from '@/assets/images/pci.png'
</script>

<template>
  <div class="form-footer">
    <div class="form-footer__top">
      <div class="form-footer__slogan">Technological solution implemented</div>
      <a href="https://platon.ua/ua" class="form-footer__logo" target="_blank">
        <img :src="Logo" alt="Platon"></a>
      <img class="form-footer__decor" :src="Master" alt="Master">
    </div>
    <div class="form-footer__logos">
      <img :src="VerifyVisa" alt="verify visa">
      <img :src="MasterCardSecure" alt="master card">
      <img :src="PCI" alt="pci">
    </div>
  </div>
</template>

<style scoped>
.form-footer {
  position: relative;
  z-index: 2;
  overflow: hidden;
  margin-left: -50px;
  font-family: "Roboto", sans-serif;
  padding-right: 50px;
  padding-bottom: 15px;
}
.form-footer__top {
  display: flex;
  justify-content: space-between;
  position: relative;
  margin-bottom: 20px;
}
.form-footer__slogan {
  position: relative;
  color: #fff;
  text-transform: uppercase;
  font-weight: 700;
  line-height: 27px;
  height: 27px;
  margin-top: 7px;
  margin-right: 15px;
  padding: 0 12px;
  text-align: right;
  background: linear-gradient(to right, #f6822d 0%, #df5b16 100%);
  flex-grow: 1;
  font-size: 12px;
}
.form-footer__slogan::after {
  content: '';
  bottom: -16px;
  height: 10px;
  width: 100%;
  position: absolute;
  left: 0;
  background: linear-gradient(to right, #f6822d 0%, #df5b16 100%);
}
.form-footer__logo {
  display: block;
  flex-shrink: 0;
  width: 184px;
}
.form-footer__decor {
  position: absolute;
  top: 13px;
  left: 10px;
}
img.form-footer__decor {
  height: auto;
}
.form-footer__logos {
  display: none;
}
@media only screen and (max-width: 640px) {
  .form-footer {
    margin: 0 -42px;
    padding-bottom: 20px;
  }
}
@media only screen and (max-width: 948px) {
  .form-footer {
    margin-left: -42px;
    padding-right: 0;
  }
}
@media only screen and (max-width: 640px) {
  .form-footer__top {
    margin-bottom: 46px;
  }
}
@media only screen and (max-width: 640px) {
  .form-footer__slogan {
    margin-right: 0;
  }
}
@media only screen and (max-width: 640px) {
  .form-footer__logo {
    display: none;
  }
}

@media only screen and (max-width: 500px) {
  .form-footer__decor {
    top: 85px;
    width: 40%;
  }
}
@media only screen and (max-width: 500px) {
  .form-footer__logos {
    float: right;
    max-width: 270px;
    width: 100%;
    align-items: end;
    flex-direction: column;
  }
}
@media only screen and (max-width: 500px) {
  .form-footer__logos img {
    margin-bottom: 10px;
  }
}

@media only screen and (max-width: 640px) {
  .form-footer__logos img {
    margin-left: 20px;
  }
}
img {
  max-width: 100%;
}
@media only screen and (max-width: 640px) {
  .form-footer__logos {
    display: flex;
    justify-content: flex-end;
    padding-right: 30px;
    align-items: flex-end;
  }
}
@media only screen and (max-width: 500px) {
  .form-footer__logos img {
    margin-bottom: 10px;
  }
}
@media only screen and (max-width: 640px) {
  .form-footer__logos img {
    margin-left: 20px;
  }
}
@media only screen and (min-width: 640px) {
  .form-footer__top {
    margin-bottom: 70px;
  }
}
</style>
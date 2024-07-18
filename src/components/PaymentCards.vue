<script setup>
import Visa from '@/assets/images/visa.svg'
import MasterCard from '@/assets/images/master-card.svg'
import Prostir from '@/assets/images/prostir.svg'
import GooglePay from '@/assets/images/googlePay.svg'
import ApplePay from '@/assets/images/applePay.svg'
import MonobankLogo from '@/assets/images/monobank-logo.png'
import Monobank from '@/assets/images/monobank.png'
import PrivatLogo from '@/assets/images/privat-logo.png'
import Privat24 from '@/assets/images/privat24.svg'
import Oschadbank from '@/assets/images/oschadbank.png'
import VerifyVisa from '@/assets/images/verify-visa.png'
import MasterCardSecure from '@/assets/images/master-card.png'
import PCI from '@/assets/images/pci.png'
</script>

<template>
 <div class="payment-cards" >
   <div class="payment-cards__row payment-cards__row--active">
    <div class="payment-cards__block">
      <div  class="payment-cards__card">
        <img :src="Visa" alt="Visa" width="70" height="25">
      </div>
      <div  class="payment-cards__card">
        <img :src="MasterCard" alt="Master Card" width="70" height="25">
      </div>
      <div  class="payment-cards__card">
        <img :src="Prostir" alt="Prostir" width="70" height="25">
      </div>
    </div>
    <button class="payments__btn"/>
  </div>
   <div class="payment-cards__row payment-cards__row--inactive">
     <div  class="payment-cards__card">
       <img :src="GooglePay" alt="GooglePay" width="72" height="29">
     </div>
     <div  class="payment-cards__card">
       <img :src="ApplePay" alt="ApplePay" width="75" height="30" class="grayscale">
     </div>
   </div>
   <div class="payment-cards__row payment-cards__row--inactive">
     <div  class="payment-cards__card">
       <img :src="MonobankLogo" alt="MonobankLogo" width="26" height="26" class="grayscale monobank-logo">
       <img :src="Monobank" alt="Monobank" width="104" height="16" class="grayscale">
     </div>
     <div  class="payment-cards__card">
       <img :src="PrivatLogo" alt="PrivatLogo" width="118" height="32" class="grayscale">
     </div>
   </div>
   <div class="payment-cards__row payment-cards__row--inactive">
     <div  class="payment-cards__card">
       <img :src="Privat24" alt="Privat24" width="126" height="29" class="grayscale">
     </div>
     <div  class="payment-cards__card">
       <img :src="Oschadbank" alt="Oschadbank" width="135" height="52" class="grayscale">
     </div>
   </div>
   <div class="payment-cards__row payment-cards__row--inactive payment-cards__row--inactive-last">
     <div  class="payment-cards__card">
       <img :src="VerifyVisa" alt="VerifyVisa" width="83" height="36" class="grayscale">
     </div>
     <div  class="payment-cards__card">
       <img :src="MasterCardSecure" alt="MasterCardSecure" width="118" height="36" class="grayscale">
     </div>
     <div  class="payment-cards__card">
       <img :src="PCI" alt="PSI" width="42" height="36" class="grayscale">
     </div>
   </div>
</div>
</template>

<style scoped>
.payment-cards__block {
  width: calc(100% - 70px);
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #fff;
  box-shadow: 0 1px 6px rgba(0, 0, 0, 0.11);
  transform: scale(1.03);
}
.payment-cards__row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 60px;
  background-color: #f5f5f5;
  transition: 0.2s ease;
  cursor: pointer;
  width: 100%;
  outline: none;
}
.payment-cards__row--inactive {
  display: none;
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
}
.payment-cards__row:nth-child(2) {
  display: flex;
}

.payment-cards__row--active .payment-cards__card {
  max-width: 33%;
}
.payment-cards__row--inactive .payment-cards__card::before {
  display: none;
}
.payment-cards__row--inactive .payment-cards__card {
  background-color: #f5f5f5;
}
.payment-cards__row--inactive .payment-cards__card:first-child {
  border-right: 1px solid rgba(0, 0, 0, 0.1);
}
.payment-cards__row--inactive-last, .payment-cards__row--inactive-last .payment-cards__card:first-child {
  border: none;
}
.payment-cards__card {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 60px;
  background-color: #ffffff;
  transition: 0.2s ease;
  cursor: pointer;
  width: 50%;
  outline: none;
}
.payments__btn {
  position: relative;
  width: 64px;
  height: 62px;
  background-color: #f26424;
  border: none;
}
.payments__btn::after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
  background: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 31.02 15.01'><polygon points='15.74 0 15.51 0.27 15.28 0 0 12.61 2.07 15.01 15.51 3.93 28.95 15.01 31.02 12.61 15.74 0' fill='rgba(255,255,255)'/></svg>") no-repeat center center;
  background-size: 31px 15px;
  transform: rotate(180deg);
}
.payment-cards__card::before {
  content: '';
  position: absolute;
  left: 0;
  top: 50%;
  margin-top: -7px;
  height: 14px;
  width: 1px;
  background-color: #ffbd95;
}
.payment-cards__card:first-child::before {
  display: none;
}
.monobank-logo {
  margin-right: 10px;
}
.grayscale {
  opacity: 0.6;
  filter: grayscale(100%);
}
@media only screen and (min-width: 948px) {
  .payment-cards__block {
    width: 100%;
  }
  .payment-cards__row--inactive {
    display: flex;
  }
  .payment-cards__card {
    background-color: #ffffff;
  }
  .payments__btn {
    display: none;
  }
}
</style>

<script setup>

</script>

<template>
  <div class="details-info">
    <div  class="details-info__item" >
      <span class="detail-order__label">Website/Store:</span>
      <span class="detail-order__value">credit_Platon.ua</span>
      <span class="detail-order__currency"></span>
    </div>
    <div  class="details-info__item" >
      <span class="detail-order__label">Order number:</span>
      <span class="detail-order__value">PL_101205423</span>
      <span class="detail-order__currency"></span>
    </div>
    <div  class="details-info__item" >
      <span class="detail-order__label">Payment amount:</span>
      <span class="detail-order__currency-value detail-order__value--primary"><strong>1.00</strong></span>
      <span class="detail-order__currency detail-order__value--primary">uah</span>
    </div>
    <div  class="details-info__item" >
      <span class="detail-order__label">Additional Services:</span>
      <span class="detail-order__currency-value detail-order__value--primary">0.00</span>
      <span class="detail-order__currency detail-order__value--primary">uah</span>
    </div>
  </div>
</template>

<style scoped>
.details-info {
  padding: 0 15px;
  margin-bottom: 30px;
}
.details-info__item {
  display: flex;
  flex-wrap: wrap;
  align-items: baseline;
  margin-bottom: 10px;
  line-height: 24px;
}
.detail-order__label {
  margin-right: 5px;
  color: #777777;
  font-size: 16px;
  font-family: "Roboto", sans-serif;
  font-weight: 500;
  flex-shrink: 0;
  background-color: #fff;
}
.detail-order__value {
  color: #000;
  font-size: 16px;
  font-family: "Roboto", sans-serif;
  font-weight: 500;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  width: auto;
}
.detail-order__currency-value {
  margin-right: 5px;
  font-size: 24px;
}
.detail-order__value--primary {
  color: #e66000;
}
</style>
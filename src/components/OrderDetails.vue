<script setup>

</script>

<template>
  <div class="order-details">
    <div class="order-details__head">
      <div class="order-details__title">Order Details</div>
    </div>
    <div class="order-details__body">
      <div class="wysiwyg wysiwyg--small">
        Оплата заказа №12345 с доставкой                                </div>
    </div>
    <div class="order-details__collapsed">
      <div class="order-details__link">
        <span class="order-details__link-show">Show all</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.order-details {
  margin-top:20px;
  padding: 10px 0;
}
.order-details__head {
  margin-bottom: 20px;
  position: relative;
  display: flex;
  justify-content: flex-start;
}
.order-details__head::before {
  position: absolute;
  content: '';
  top: 50%;
  height: 1px;
  width: 100%;
  right: 0;
  background-color: #dcdcdc;
}
.order-details__title {
  position: relative;
  font-size: 16px;
  line-height: 10px;
  color: #777;
  padding-right: 8px;
  background: #fff;
  z-index: 2;
}
.order-details__body {
  position: relative;
  max-height: 80px;
  overflow: hidden;
}
.wysiwyg--small {
  font-size: 12px;
}

.wysiwyg {
  color: #777777;
  line-height: 1.2em;
  font-family: "Roboto", sans-serif;
}
.order-details__body::after {
  position: absolute;
  bottom: 0;
  content: '';
  left: 0;
  width: 100%;
  height: 30px;
  pointer-events: none;
  background: linear-gradient(to bottom, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 1) 100%);
}
.order-details__collapsed {
  display: flex;
  justify-content: flex-end;
}
.order-details__link {
  font-size: 16px;
  color: #f26424;
  line-height: 20px;
  padding-right: 24px;
  cursor: pointer;
  position: relative;
}
.order-details__link::after {
  position: absolute;
  content: '';
  right: 0;
  top: 50%;
  margin-top: -4px;
  width: 16px;
  height: 7px;
  background: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 31.02 15.01'><polygon points='15.74 0 15.51 0.27 15.28 0 0 12.61 2.07 15.01 15.51 3.93 28.95 15.01 31.02 12.61 15.74 0' fill='rgba(242,100,36)'/></svg>") no-repeat right center;
  background-size: 16px 7px;
  transform: rotate(180deg);
}
</style>
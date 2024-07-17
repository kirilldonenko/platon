<template>
  <div id="app">
    <div class="section">
      <div class="container">
        <PaymentDetails />
        <PaymentForm />
      </div>
    </div>
  </div>
</template>

<script setup>
import PaymentForm from "@/components/PaymentForm.vue";
import PaymentDetails from "@/components/PaymentDetails.vue";
</script>

<style>
#app {
  font-family: system-ui, -apple-system, Segoe UI, Roboto, Helvetica Neue, Arial, Noto Sans, Liberation Sans, sans-serif, Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol, Noto Color Emoji;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
.section {
  padding: 15px 0;
  box-shadow: 0 23px 79px rgba(0, 0, 0, 0.16);
}
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
  padding: 0 10px;
}
@media only screen and (min-width: 950px) {
  .container {
    flex-direction: row;
  }
}
</style>

<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Btc from '@/components/Btc.vue'
import Eth from '@/components/Eth.vue'
import LocationTemp from '@/components/LocationTemp.vue'
</script>

<template>
  <header>
    

    <div class="wrapper">
      <LocationTemp />
      <Eth />
      <Btc />
    </div>
  </header>

  
</template>

<style>
@import '@/assets/base.css';

.div {
  width: 40%;
  padding: 20px;
  border: solid 1px;
  border-color: rgb(105, 81, 133);
  display: flex;
  flex-wrap: wrap;
  align-items: start;
  justify-content: start;
}

.text {
  color: rgb(105, 81, 133);
  font-size: 30px;
  text-transform: uppercase;
}

.img {
  width: 10%;
}

.marg-text {
  margin: 0 20px 0 80px;
}

.marg {
  margin: 0 20px 0 50px;
}
</style>

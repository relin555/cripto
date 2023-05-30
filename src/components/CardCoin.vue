<script setup>
import { ref, defineProps } from 'vue';
const cur = defineProps( {
  currency: String
})

const price = ref('')

const key = '4e8a04e0c5a6734a6b7dd4748eac05d46d1f56ef49d810650478a9043d556fca';
setInterval(  async () =>
{
  let coin = await fetch( `https://min-api.cryptocompare.com/data/price?fsym=${ cur.currency.currency }&tsyms=USD,EUR&api_key=${ key }` );
  let data = await coin.json();  
  price.value = data.USD;
}, 5000 );

</script>
<template>
  <div class="home__coin-card">
    <img src="" alt="" />
    <h1 class="home__coin-name">{{ cur.currency.currency }}</h1>  
    <h2 class="home__coin-price">{{ price !== '' ? price : 'load' }}</h2>
  </div>
</template>
<script setup>
import { ref } from 'vue';
import FormComponent from '@/components/FormComponent.vue';
import MyBtn from '@/components/UI/MyBtn.vue'

const inputValue = ref( '' );
const btcCurrency = ref( '' );
const key = ref( '4e8a04e0c5a6734a6b7dd4748eac05d46d1f56ef49d810650478a9043d556fca' );
setInterval( async () =>
{
  const blockChain = await fetch( `https://min-api.cryptocompare.com/data/price?fsym=${inputValue.value}&tsyms=USD,EUR&api_key=${key}`
  );
  const data = await blockChain.json();
  btcCurrency.value = data.USD
}, 5000 );

const getValueBtc = ( value ) =>
{
  inputValue.value = value.value
};
const criptoCurrency = [
  { currency: 'ETH' },
  { currency: 'BTN' },
  { currency: 'BUSD' },
  { currency: 'CFX' },
  { currency: 'BTC' },
];
const changeCurrencyCoin = (currency) =>
{
  inputValue.value = currency
}
</script>
<template>
  <div class="home">
    <div class="home__inner">
      <div class="home__change-coin">
        <MyBtn @click="changeCurrencyCoin(item.currency)" v-for="item in criptoCurrency" :key="item.currency">{{ item.currency }}</MyBtn>
      </div>
      <FormComponent @getValueBtc="getValueBtc"/>
    </div>
    {{ btcCurrency }}
  </div>
</template>

<style scoped>
  
</style>
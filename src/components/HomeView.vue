<script setup>
import { ref } from 'vue';
import FormComponent from '@/components/FormComponent.vue'

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
</script>
<template>
  <div class="home">
    <div class="home__inner">
      <FormComponent @getValueBtc="getValueBtc"/>
    </div>
    
  </div>
</template>

<style scoped>
  .home__cards  {
    display: flex;
    flex-wrap: wrap;
  }
  .home__card {
    border: 1px solid grey;
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 300px;
    height: 400px;
    padding: 15px;
    margin: 10px;
  }
  .home__card > img {
    width: 150px;
    bottom: 15px;
  }
  .home__card > h1 {
    font-size: 20px;
  }
</style>
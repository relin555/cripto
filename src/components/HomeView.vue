<script setup>
import { ref } from 'vue';
import FormComponent from '@/components/FormComponent.vue';
import MyBtn from '@/components/UI/MyBtn.vue'
import CardCoin from '@/components/CardCoin.vue'

const criptoCurrency = [
  { currency: 'ETH' },
  { currency: 'BTN' },
  { currency: 'BUSD' },
  { currency: 'CFX' },
  { currency: 'BTC' },
];

const cardCoin = ref( [] );



const changeCurrencyCoin = ( currency ) =>
{
  cardCoin.value.push(
   { currency: currency }
  )
};
</script>
<template>
  <div class="home">
    <div class="home__inner">
      <div class="home__change-coin">
        <MyBtn 
          @click="changeCurrencyCoin(item.currency)" 
          v-for="(item,idx) in criptoCurrency" 
          :key="idx">
            {{ item.currency }}
        </MyBtn>
      </div>
      <div class="home__form">
        <FormComponent @getValueBtc="getValueBtc"/>
      </div>
      <div class="home__coin-cards">
        <CardCoin v-for="(item,idx) in cardCoin" :key="idx" :currency="item"/>
      </div>
    </div>
  </div>
</template>

<style scoped>
  
</style>
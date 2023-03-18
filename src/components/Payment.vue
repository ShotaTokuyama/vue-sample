<script setup lang="ts">
import { ref, reactive, computed } from 'vue'

const url1 = 'https://www.amazon.co.jp/'

const buy = (itemName: string) => {
  alert('buy' + itemName)
}

const item1 = reactive ({
  name: 'Desk',
  price: 40000,
})

const item2 = reactive ({
  name: 'Bike',
  price: 20000,
}) 


const clear = () => {
  item1.name = ""
  item1.price = 0
}

const budget = 50000
const priceLabel = computed(() => {
  if(item1.price > budget) {
    return 'too expensive...'
  } else {
    return item1.price + 'yen'
  }
})
</script>

<template>
  <div class="container">
    <h1>最近の支出</h1>
    <div class=""></div>
    <label for="itemName">アイテム</label>
    <input v-model="item1.name">
    <label for="itemPrice">価格</label>
    <input v-model="item1.price"/>
    <button v-on:click="clear">Clear</button>
    <div class="payment">
      <label>{{ item1.name }}</label>
      <label>{{ priceLabel }}</label>
      <a v-bind:href="url1">bought at...</a>
      <button v-on:click="buy(item1.name)">BUY</button>
    </div>
    <div class="payment">
      <label>{{ item2.name }}</label>
      <label>{{ item2.price }} yen</label>
      <button v-on:click="buy(item2.name)">BUY</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.payment {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 400px;
  height: 80px;
  background-color: pink;
}

input {
  margin-bottom: 8px;
}

label {
  font-size: 20px;
  font-weight: bold;
}
</style>

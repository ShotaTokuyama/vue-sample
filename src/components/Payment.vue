<script setup lang="ts">
import { ref, reactive, computed } from "vue";

const url1 = "https://www.amazon.co.jp/";

const buy = (itemName: string) => {
  alert("buy" + itemName);
};

const item1 = reactive({
  name: "Desk",
  price: 40000,
});

const item2 = reactive({
  name: "Bike",
  price: 20000,
});

const clear = () => {
  item1.name = "";
  item1.price = 0;
};

const budget = 50000;
const priceLabel = computed(() => {
  if (item1.price > budget) {
    return "too expensive...";
  } else {
    return item1.price + "yen";
  }
});
</script>

<template>
  <div class="flex flex-col items-center container">
    <h1 class="mt-10 mb-6 text-x3 font-bold">最近の支出</h1>
    <input class="border-gray-600 border mb-4" v-model="item1.name" />
    <input class="border-gray-600 border mb-4" v-model="item1.price" />
    <button class="mb-6 font-bold border-gray-600 border" v-on:click="clear">Clear</button>
    <div class="flex justify-between items-center w-96 h-20 bg-red-200">
      <label class="text-xl font-bold">{{ item1.name }}</label>
      <label class="text-xl font-bold">{{ priceLabel }}</label>
      <a v-bind:href="url1">bought at...</a>
      <button class="border-gray-600 border p-1" v-on:click="buy(item1.name)">BUY</button>
    </div>
    <div class="flex justify-between items-center w-96 h-20 bg-red-200">
      <label class="text-xl font-bold">{{ item2.name }}</label>
      <label class="text-xl font-bold">{{ item2.price }} yen</label>
      <button class="border-gray-600 border p-1" v-on:click="buy(item2.name)">BUY</button>
    </div>
  </div>
</template>

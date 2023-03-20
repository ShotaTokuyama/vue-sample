<script setup lang="ts">
import { defineProps } from 'vue';
type Tweet = {
  id: number,
  description: string

}
type Props = {
  tweets: Tweet[]
}

const deleteTweet = (id: number) => {};
defineProps<Props>()
</script>
<template>
  <li
    v-for="tweet in tweets"
    :key="tweet.id"
    class="list-none text-xl mb-2 flex justify-between bg-yellow-300 w-full py-2 px-5"
  >
    <span>{{ tweet.description }}</span>
    <button @click="deleteTweet(tweet.id)" class="button bg-red-600">
      delete
    </button>
  </li>
</template>

<script setup lang="ts">
import { ref } from "vue";
import TweetPostForm from './TweetPostForm.vue'
import TweetList from './TweetList.vue'

const tweets = ref([
  { id: 0, description: "Hellow,World!" },
  { id: 1, description: "this is the second tweet" },
]);

const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter(t => t.id !== id)
}
</script>

<template>
  <div class="flex flex-col items-center container">
    <h1 class="mt-10 mb-6 text-5xl font-bold">Tweeter</h1>
    <TweetPostForm/>
    <div class="flex flex-col items-center py-6 w-4/5 mb-2">
      <p v-if="tweets.length <= 0">No tweet have been added</p>
      <ul v-else class="w-3/5">
        <TweetList :tweets="tweets"/>
      </ul>
    </div>
  </div>
</template>

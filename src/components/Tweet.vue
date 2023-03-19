<script setup lang="ts">
import { ref } from "vue";

const tweets = ref([
  { id: 0, description: "Hellow,World!" },
  { id: 1, description: "this is the second tweet" },
]);

const inputingDescription = ref<string>("");

const postTweet = () => {
  const tweet = { id: Math.random(), description: inputingDescription.value };
  inputingDescription.value = "";
  tweets.value.push(tweet);
};

const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter(t => t.id !== id)
}
</script>

<template>
  <div class="flex flex-col items-center container">
    <h1 class="mt-10 mb-6 text-5xl font-bold">Tweeter</h1>
    <div class="flex flex-col items-center bg-blue-400 py-6 w-3/5 mb-2">
      <input
        v-model="inputingDescription"
        class="border-gray-600 border mb-4"
        type="text"
      />
      <button @click="postTweet()" class="button bg-red-600">post</button>
    </div>
    <div class="flex flex-col items-center py-6 w-4/5 mb-2">
      <p v-if="tweets.length <= 0">No tweet have been added</p>
      <ul v-else class="w-3/5">
        <li
          v-for="tweet in tweets"
          :key="tweet.id"
          class="list-none text-xl mb-2 flex justify-between bg-yellow-300 w-full py-2 px-5"
        >
          <span>{{ tweet.description }}</span>
          <button @click="deleteTweet(tweet.id)" class="button bg-red-600">delete</button>
        </li>
      </ul>
    </div>
  </div>
</template>

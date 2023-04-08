<script setup lang="ts">
import { ref, defineEmits } from "vue";

const inputtingDescription = ref<string>('');
const emit = defineEmits(['post-tweet'])
const postTweet = () => {
  emit('post-tweet',inputtingDescription.value)
}
</script>

<template>
  <div class="flex flex-col items-center bg-blue-400 py-6 w-3/5 mb-2">
    <input
      v-model="inputtingDescription"
      class="border-gray-600 border mb-4"
      type="text"
    />
    <button @click="postTweet()" class="button bg-red-600">post</button>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
const inputtingName = ref<string>('')
const inputtingAge = ref<number>(0)

const emit = defineEmits(['register'])

const register = () => {
  const person = { id: Math.random(), name: inputtingName.value, age: inputtingAge.value }

  emit('register', person)
}
</script>
<template>
  <div>こん</div>
  <div>
    <div class="flex flex-col items-center bg-blue-400 py-6 w-3/5 mb-2">
      <div>
        <label>name:</label>
        <input class="border-gray-600 border mb-4" type="text" v-model="inputtingName"/>
      </div>
      <div>
        <label>age:</label>
        <input class="border-gray-600 border mb-4" type="number" v-model="inputtingAge"/>
      </div>
    </div>
    <button  @click="register()" class="button bg-red-600">register</button>
  </div>
</template>

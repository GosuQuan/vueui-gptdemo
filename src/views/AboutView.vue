<template>
  <input v-model="inputValue" />
  {{ data }}
  <div>{{ count }}</div>
  <button @click="handleOnclick">按我
  </button>

</template>

<script setup>
import { ref } from 'vue'
import axios from 'axios'
const count = ref(0)
const inputValue = ref('')
const data = ref('')
const handleOnclick = async () => {
  const eventSource = new EventSource("http://localhost:9000/chat")
  data.value = await axios.get("http://localhost:9000/chat")
    .then((res => res.data))
  
    .catch(function (error) {
      console.log(error)
    })

}


</script>
<template>
  <section>
    <h2>{{ msg }}</h2>
    <p>Counter: {{ count }}</p>
    <button @click="increment">Increment</button>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps<{ msg: string }>()
const count = ref(0)
function increment() {
  count.value++
}

const msg = props.msg
</script>

<style scoped>
button {
  padding: 0.5rem 1rem;
  background: #3b82f6;
  color: white;
  border: none;
  border-radius: 4px;
}
</style>

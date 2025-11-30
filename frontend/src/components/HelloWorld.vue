<template>
  <section>
    <h2>{{ msg }}</h2>
    <p>Counter: {{ count }}</p>
    <button @click="increment">Increment</button>
    
    <hr />
    <NewComponent v-model="childCount" title="Child Component from HelloWorld" description="This is a child component." />
    <p>Child count (from child): {{ childCount }}</p>
  </section>
</template>

<script setup lang="ts">
import { ref, defineAsyncComponent } from 'vue'
const NewComponent = defineAsyncComponent(() => import('./newComponent.vue'))

const props = defineProps<{ msg: string }>()
const count = ref(0)
const childCount = ref(0)
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

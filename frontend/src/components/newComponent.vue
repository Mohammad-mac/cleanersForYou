<template>
    <div class="new-component">
        <h3>{{ title }}</h3>
        <p v-if="description">{{ description }}</p>

        <div class="controls">
            <button @click="decrement" aria-label="decrement">-</button>
            <span class="count">{{ count }}</span>
            <button @click="increment" aria-label="increment">+</button>
        </div>
    </div>
</template>

<script setup>
import { ref, watch } from 'vue'

const props = defineProps({
    title: { type: String, default: 'Child Component' },
    description: { type: String, default: '' },
    modelValue: { type: Number, default: 0 } // use v-model in parent: <NewComponent v-model="n" />
})

const emit = defineEmits(['update:modelValue'])

const count = ref(props.modelValue)

watch(() => props.modelValue, (v) => (count.value = v))

function increment() {
    count.value++
    emit('update:modelValue', count.value)
}
function decrement() {
    count.value--
    emit('update:modelValue', count.value)
}
</script>

<style scoped>
.new-component {
    border: 1px solid #e6e6e6;
    padding: 12px;
    border-radius: 6px;
    max-width: 280px;
}
.controls {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    margin-top: 8px;
}
.count {
    min-width: 28px;
    text-align: center;
    display: inline-block;
}
button {
    padding: 4px 8px;
    cursor: pointer;
}
</style>
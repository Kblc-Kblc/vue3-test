<template>
  <div>
    <h3>TheCounter</h3>
    <slot name="default" :count="count">
      <p>Count: {{ count }}</p>
    </slot>
    <button @click="$emit('count-incremented')">Click me</button>
  </div>
</template>

<script setup lang="ts">
import { defineProps } from 'vue'

const props = defineProps({
  count: Number
})
</script>

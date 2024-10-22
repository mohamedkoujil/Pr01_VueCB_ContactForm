<script setup>
import { defineEmits } from 'vue'
const emit = defineEmits(['searchContact'])

const searchContact = ({ target }) => {
  emit('searchContact', target.value)
}
</script>

<template>
  <div>
    <input @input="searchContact" placeholder="Search contact" />
  </div>
</template>

<style scoped></style>

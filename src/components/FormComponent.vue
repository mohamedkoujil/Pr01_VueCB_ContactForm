<script setup>
const emit = defineEmits(['addContact'])

function handleSubmit(event) {
  event.preventDefault()
  const contact = {
    name: event.target.name.value,
    numero: event.target.numero.value
  }
  emit('addContact', contact)
}
</script>

<template>
  <form @submit="handleSubmit">
    <input type="text" placeholder="Nom del contacte" name="name" required />
    <input type="number" placeholder="Número de telèfon" name="numero" required />
    <button type="submit">Afegir contacte</button>
  </form>
</template>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  padding: 1rem;
  background-color: rgba(140, 140, 255, 0.596);
  border-radius: 15px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  margin: 1em;
  max-height: 115px;
}
</style>

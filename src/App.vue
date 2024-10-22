<script setup>
import { ref } from 'vue'
import FormComponent from './components/FormComponent.vue'
import ContactList from './components/ContactList.vue'

const contacts = ref([
  { name: 'Pepito', numero: 123456789 },
  { name: 'Fulanito', numero: 987654321 },
  { name: 'Menganito', numero: 123123123 }
])

const addContact = (contact) => {
  const exists = contacts.value.find((c) => c.numero === contact.numero)
  if (exists) {
    alert('Aquest número ja existeix')
    return
  }
  contacts.value = [...contacts.value, contact]
}
</script>

<template>
  <h1>Llibreta de contactes</h1>
  <div class="container">
    <FormComponent @addContact="addContact" />

    <div>
      <ContactList :contacts="contacts" />
    </div>
  </div>
</template>

<style scoped>
h1 {
  text-align: center;
}
.container {
  display: flex;
  justify-content: center;
}
</style>

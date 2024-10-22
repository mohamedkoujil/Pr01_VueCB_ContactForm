<script setup>
import { computed, ref } from 'vue'
import SearchContact from './SearchContact.vue'

const { contacts } = defineProps(['contacts'])
const searchedContact = ref('')

const searchContact = (value) => {
  searchedContact.value = value
}

const filteredContacts = computed(() => {
  return contacts?.filter((contact) => {
    console.log(contact.name.toLowerCase().includes(searchedContact.value.toLowerCase()))
    return contact.name.toLowerCase().includes(searchedContact.value.toLowerCase())
  })
})
</script>

<template>
  <div class="container">
    <h2>Contactes</h2>
    <SearchContact @searchContact="searchContact" />
    <ul>
      <li v-for="contact in filteredContacts" :key="contact.numero">
        {{ contact.name }} - <span>{{ contact.numero }}</span>
      </li>
    </ul>
  </div>
</template>

<style scoped>
div {
  color: white;
}
.container {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  padding: 1rem;
  background-color: rgba(140, 140, 255, 0.596);
  border-radius: 15px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  margin: 1em;
}
ul {
  list-style: none;
  padding: 0;
}
li {
  display: flex;
  justify-content: space-between;
  padding: 0.5rem;
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
}
span {
  font-weight: bold;
}
</style>

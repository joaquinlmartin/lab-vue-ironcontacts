<template>
  <h1>Iron Contacts</h1>
  <button @click="addContact" class="btn">Add Random Contact</button>
  <button @click="sortByPopularity" class="btn">Sort by popularity</button>
  <button @click="sortByName" class="btn">Sort by name</button>
  <table>
    <tr class="first-TR">
      <th><h2>Picture</h2></th>
      <th><h2>Name</h2></th>
      <th><h2>Popularity</h2></th>
      <th><h2>Won Oscar</h2></th>
      <th><h2>Won Emmy</h2></th>
      <th><h2>Actions</h2></th></tr>
    <tr v-for="item in contactsShown" :key="item.id" class="second-TR">
    <td><img :src="item.pictureUrl" class="image" alt="image" /></td>
    <td>{{item.name}}</td>
    <td>{{item.popularity}}</td>
    <td><p v-if="item.wonOscar">🏆</p></td>
    <td><p v-if="item.wonEmmy">🏆</p></td>
    <td><button @click="() => deleteContact(item.id)">Delete</button></td>
    </tr>
  </table>
</template>

<script setup>
import { ref } from 'vue';
import contactsData from './contacts.json';

const contactsShown = ref(contactsData.slice(0, 5));
const contactsLeft = ref(contactsData.slice(6, contactsData.length));

const addContact = () => {
  const randomInt = Math.floor(Math.random() * contactsLeft.value.length);
  const newContact = contactsLeft.value[randomInt];
  contactsLeft.value.splice(randomInt, 1);
  contactsShown.value.unshift(newContact);
};

const sortByPopularity = () => {
  contactsShown.value.sort((a, b) => {
    if (a.popularity < b.popularity) { return 1; }
    if (a.popularity > b.popularity) { return -1; }
    return 0;
  });
};

const sortByName = () => {
  contactsShown.value.sort((a, b) => {
    if (a.name < b.name) { return -1; }
    if (a.name > b.name) { return 1; }
    return 0;
  });
};

const deleteContact = (id) => {
  const filteredContacts = contactsShown.value.filter((contact) => contact.id !== id);
  contactsShown.value = filteredContacts;
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.image {
  height: 140px;
  width: auto;
}

.btn {
 color: white;
 background-color: rgb(194, 161, 14);
 border-radius: 1rem;
 border-width: 0;
 margin: 8px;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

h1{
  color: rgb(194, 161, 14);

}

table {
  width: 100%;
  border: 2px solid rgb(194, 161, 14);
  border-collapse: collapse;
  row-gap: 5px;
  column-gap: 5px;
}

.first-TR {
  border-bottom: 4px solid rgb(194, 161, 14);
}

tr{
  border: 2px solid rgb(194, 161, 14);
}

td {
  border: 2px solid rgb(194, 161, 14);
}

th{
  border-left: 4px solid rgb(194, 161, 14);
  color: white;
  background-color: rgb(194, 161, 14);
}
</style>

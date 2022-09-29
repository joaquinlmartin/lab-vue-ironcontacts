<template>
  <h1>Iron Contacts</h1>
  <table>
    <tr class="first-TR">
      <th>
        <h2>Picture</h2>
      </th>
      <th>
        <h2>Name</h2>
      </th>
      <th>
        <h2>Popularity</h2>
      </th>
      <th>
        <h2>Won Oscar</h2>
      </th>
      <th>
        <h2>Won Emmy</h2>
      </th>
       <th>
        <h2>Actions</h2>
      </th>
    </tr>
    <tr v-for="item in contacts" :key="item.id" class="second-TR">
    <td><img :src="item.pictureUrl" class="image" alt="" /></td>
    <td>{{item.name}}</td>
    <td>{{item.popularity}}</td>
    </tr>
  </table>
</template>

<script>
import contacts from './contacts.json';

export default {
  data() {
    return {
      contactsBD: contacts,
      contactsSize: 5,
      contacts: [
        {
          name: 'Idris Elba',
          pictureUrl: 'https://image.tmdb.org/t/p/w500/d9NkfCwczP0TjgrjpF94jF67SK8.jpg',
          popularity: 11.622713,
          id: '11731993-0604-4bee-80d5-67ad845d0a38',
          wonOscar: false,
          wonEmmy: false,
        },
        {
          name: 'Johnny Depp',
          pictureUrl: 'https://image.tmdb.org/t/p/w500/kbWValANhZI8rbWZXximXuMN4UN.jpg',
          popularity: 15.656534,
          id: '7dad00f7-3949-477d-a7e2-1467fd2cfc06',
          wonOscar: false,
          wonEmmy: false,
        },
        {
          name: 'Monica Bellucci',
          pictureUrl: 'https://image.tmdb.org/t/p/w500/qlT4904d8oi2NIs28RrgnIZDFZB.jpg',
          popularity: 16.096436,
          id: '0ad5e441-3084-47a1-9e9b-b917539bba71',
          wonOscar: false,
          wonEmmy: false,
        },
        {
          name: 'Gal Gadot',
          pictureUrl: 'https://image.tmdb.org/t/p/w500/34kHAyBaBhq2kUrmhM15paEBuuI.jpg',
          popularity: 10.049256,
          id: 'b497e3c4-50bb-4ae2-912f-eb36802c5bc2',
          wonOscar: false,
          wonEmmy: false,
        },
        {
          name: 'Ian McKellen',
          pictureUrl: 'https://image.tmdb.org/t/p/w500/coWjgMEYJjk2OrNddlXCBm8EIr3.jpg',
          popularity: 10.070132,
          id: '0067ae32-97b6-4431-898e-eb1c10150abb',
          wonOscar: false,
          wonEmmy: false,
        },
      ],
    };
  },
  components: { },
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

btn {
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
  color: gold;

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

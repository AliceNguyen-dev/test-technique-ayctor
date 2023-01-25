<template>
  <div>

    <div class="titleName"><h1>Bonjour {{ title }} {{ first }} {{ last }}</h1></div>

    <div class="bloc-select">
      <p class="text-select">Séléctionner un nouveau profil à l'aide de cette liste :</p>
      <select class="s-user" v-model="selectedUser" @change="fetchData" name="randomuser">
        <option v-for="user in users" :value="user.id" :key="user.id">{{ user.name.first }} {{ user.name.last }}</option>
      </select>
    </div>

    <div class="img-user">
      <img v-bind:src="picture" :alt="`${first} ${last}`" />
    </div>

    <div class="btn-div">
      <button class="btnSelect">Afficher sa photo de profil</button>
    </div>
    
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: "App",
  components: {},
  data() {
      return {
        selectedUser: '',
        users: []
      }
    },
    methods: {
      fetchData() {
        axios.get(`https://randomuser.me/api/?results=100`)
          .then(response => {
            this.users = response.data.results
          })
      }
    },
    created() {
      this.fetchData()
    }

  
}
</script>

<style>

.app{
    display: flex;
    justify-content: center;
    margin: 215px auto;
}

h1{
    font-size: 47px;
    font-weight: 600;
    font-family: 'Roboto Slab', serif;
    color:#414047;
}

.text-select{
    font-size: 17px;
    font-family: 'Roboto Slab', serif;
    font-weight: 600;
    color: #000000ba;
}

.profil-img{
    width: 400px;
    border-radius: 195px;
}



.btn-profil{
    background: black;
    color: white;
    width: 321px;
    height: 44px;
    border-radius: 15px;
    font-size: 16px;
    text-transform: uppercase;
    margin: 10px;
}

.name-title{
    text-transform: uppercase;
    font-size: 45px;
    font-family: 'Roboto Slab', serif;
    color: #414047;
}

.bloc-select{
  display:flex;
}

.s-user{
  height: 22px;
  margin: 17px;
}
</style>

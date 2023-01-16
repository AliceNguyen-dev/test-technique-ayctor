<template>
  <div class="app">
    <div class="text-select box-left">

        <h1>Bonjour <br/> <span class="name-title">{{ firstName }} {{ lastName }}</span></h1>

        <p class="text-select">Séléctionner un nouveau profil à l'aide de cette liste : 
            <select v-model="selected">
            <option disabled value="">{{ selected }}</option>
            <option @click="getUser()">{{ firstName }} {{ lastName }}</option>
            </select>
        </p>


        <button class="btn-profil" @click="getUser()">Afficher sa photo de profil </button>

    </div>

    <div class="box-right">
        <div class="profil-pict"></div>
        <div class="angle-face"></div>
    </div>
    

    
  </div>
</template>

<script>
import img from "../assets/blueEyes.png";
export default {
  name: "App",
  components: {},
  data() {
    return {
      firstName: "Amir",
      lastName: "Danish",
      picture: img,
    };
  },
  methods: {
    async getUser() {
      const res = await fetch("https://randomuser.me/api");
      const { results } = await res.json();

      // console.log(results)

      this.firstName = results[0].name.first;
      this.lastName = results[0].name.last;
      this.picture = results[0].picture.large;
    },
  },
};
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
</style>

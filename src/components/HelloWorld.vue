<template >
<div >
    <div>
      <p>Voici des informations sur un Pokémon :</p>

      <div v-for="(unPokemon, index) in unPokemon" :key="index">
        <p>{{ unPokemon.name }}
        {{ unPokemon.order}}</p>
      </div>
    </div> <br> <br> <br>

    <p>Recherchez un Pokemon par son ID : <input type="number" id="pokeId" placeholder="Pokemon ID" min="0" max="898" />
        <button class="btn" v-on:click="cherchePoke">Rechercher</button></p>

      <div v-if="this.pokeInfos">
          <div> <p>Nom : {{this.pokeInfos.name}}</p> </div>
                    <img id='src' >
          <div> <p>Taille : {{this.pokeInfos.height}} pouces</p> </div>
          <div> <p>Poids : {{this.pokeInfos.weight}} kilogrammes</p> </div>

      </div>
</div>

</template>

<script>

import axios from 'axios'

export default {
  name: 'Poke App',
  data () {
    return {
      unPokemon: null,
      pokeInfos: null,

      pokeId: 0,
    }
  },

  mounted () {
    axios
    .get('https://pokeapi.co/api/v2/pokemon/ditto')
    .then(response =>{
      this.unPokemon = response
      })
    },

  methods: {
      cherchePoke: function() {
          console.log(this.pokeId);
          axios
              .get('https://pokeapi.co/api/v2/pokemon/'+document.getElementById('pokeId').value)
              .then(response => {

                this.pokeInfos = response.data

                var imgPoke = document.getElementById('src')
                imgPoke.src = this.pokeInfos.sprites.front_default

                })
              .catch(error => console.log(error))
      },
    },
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

p{
  font-weight: bold;
}

main{
  width: 100vw;
  height: 100vh;
}

.btn{
  background-color: #4CAF50; /* Green */
  border: none;
  border-radius: 50px;
  color: white;
  padding: 7px 16px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-weight: bold;
  font-size: 15px;
}

.content{
justify-content: center;
height: 50%;
width: 30%;
background-color: white;
}
</style>

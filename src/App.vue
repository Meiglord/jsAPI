<template>
  <div id="app">
    <img class="pkm" src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/International_Pok%C3%A9mon_logo.svg/1200px-International_Pok%C3%A9mon_logo.svg.png">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>

html, body {
  margin:0px;
  height:100%;
}

.pkm{
  margin-top: 2%;
  width: auto;
  height: 30%;
}

#app {
  height: 100vh;
  /* width: 100vw; */
  background-image: url(../pokemonbg.png) ;
  background-repeat: no-repeat;

  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>

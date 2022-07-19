<template>
  <MainMenu></MainMenu>
  <Pokemain></Pokemain>
</template>

<script>
import Pokemain from '/src/views/PokeMain.vue'
import MainMenu from '/src/views/MainMenu.vue'

export default {
  name: 'App',
  components: {
    Pokemain,
    MainMenu
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-family: 'Montserrat', sans-serif;
  font-family: 'Roboto', sans-serif;
  margin: 0;
}
</style>

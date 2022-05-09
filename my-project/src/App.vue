<template>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>POKEDEX</title>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;700&family=Roboto:wght@100;300;500&display=swap" rel="stylesheet">
</head>
<body>
  <Pokemain></Pokemain>
</body>
</html>
  
</template>

<script>
import Pokemain from './components/PokeMain.vue'

export default {
  name: 'App',
  components: {
    Pokemain
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
}
</style>

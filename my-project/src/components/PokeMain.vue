<template>
  <div class="main-div">
    <div class="pokemon-container" v-for="pokemon in pokemons" :key="pokemon.name">
			<h3>#{{pokemon.id}}</h3>
			<div class="pokemon-info-container">
				<img :src="pokemon.img.other.dream_world.front_default" :alt="pokemon.name">{{pokemon.name}}</div>
    </div>
  </div>
</template>

<script>
import PokemonRepository from "@/services/PokemonRepository.vue";
export default {
  name: 'PokeMain',
  data() {
		return {
      pokemons:[]
		};
	},
  async created() {
		//let vm = this;
		const pokemonApi = new PokemonRepository();
		pokemonApi.getPokemonLimit().then(async resp => {
      resp.data.results.forEach(element => {
        pokemonApi.getPokemon(element.name).then(resposta => {
        element.img = resposta.data.sprites;
				element.id = resposta.data.id
        this.pokemons.push(element);
			});
     });
		})
    console.log(this.pokemons)
	},
  methods: {
    }
}
</script>

<style lang="css" scoped>
body{
	margin:0;
	padding: 0;
	box-sizing: border-box;
}
.main-div{
	display: flex;
  max-width: 1000px;
  height: auto;
  flex-flow: wrap;
  justify-content: space-between;
	margin: auto;
}
.pokemon-container{
	display: flex;
  align-items: baseline;
	padding: 20px;
	margin-bottom: 60px;
  border-top-left-radius: 10px;
  border-bottom-right-radius: 10px;
	border: 1px solid lightgray;
  box-shadow: 0px 35px 50px rgb(0 0 0 / 20%);
}
.pokemon-info-container{
	display: flex;
  flex-flow: column;
  height: 180px;
  align-items: center;
  justify-content:center;
}
.pokemon-info-container img {
	width:100px ;
	height: 100px;
}
</style>


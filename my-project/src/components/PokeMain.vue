<template>
  <div class="main-div">
		<div class="button-container">
			<a href="#" class="previous round" @click="getPokemonsData(previous)">&#8249;</a>
			<a href="#" class="next round" @click="getPokemonsData(next)">&#8250;</a>
		</div>
    <div class="pokemon-container" v-for="pokemon in pokemons" :key="pokemon.name">
			<div class="title">
				<span>{{ upperCase(pokemon.name) }}</span>
			<img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/items/poke-ball.png" alt=""></div>
			<div class="pokemon-info-container">
				<h3>#{{pokemon.id}}</h3>
				<img :src="pokemon.img.other['official-artwork'].front_default" :alt="pokemon.name">
			</div>
    </div>
  </div>
</template>

<script>
import PokemonRepository from "@/services/PokemonRepository.vue";
export default {
  name: 'PokeMain',
  data() {
		return {
      pokemons:[],
			next:'',
			previous:'',
		};
	},
  async created() {
		this.limit = '?offset=0&limit=151'
		this.getPokemonsData(this.limit);

	},
  methods: {

		upperCase: function(parameter){
			return parameter.toUpperCase()
		},

		getPokemonsData: function(limit){
			this.pokemons = [];
			const pokemonApi = new PokemonRepository();
			pokemonApi.getPokemonLimit(limit).then(async resp => {
			let links = resp.data;
			console.log(links);
			if(links.next){
				this.next = links.next.substring(34);
			}else{
				this.next = '?offset=0&limit=151';
			}
			if(links.previous){
				this.previous = links.previous.substring(34);
			}else{
				this.previous = '?offset=0&limit=151';
			}
			console.log(this.next,this.previous)
				resp.data.results.forEach(element => {
					pokemonApi.getPokemon(element.name).then(resposta => {
					element.img = resposta.data.sprites;
					element.id = resposta.data.id
					this.pokemons.push(element);
				});
			});
		})
			console.log(this.pokemons)
		}

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
.button-container{
	width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.next{
	position: fixed;
  right: 13%;
  margin-top: 50%;
}
.previous{
	position: fixed;
  left: 13%;
  margin-top: 50%;
}
a {
  text-decoration: none;
  display: inline-block;
  padding: 8px 16px;
}

a:hover {
  background-color: #ddd;
  color: black;
}

.previous {
  background-color: #f1f1f1;
  color: black;
}

.next {
  background-color: #bca136;
  color: white;
}

.round {
  border-radius: 50%;
}
.pokemon-container{
	display: flex;
  align-items: baseline;
	flex-flow: column;
  width: 150px;
  height: 200px;
	margin-bottom: 60px;
  border-top-left-radius: 20px;
  border-bottom-right-radius: 20px;
  box-shadow: 0px 35px 50px rgb(0 0 0 / 20%);
	transition: ease-in 0.3s;
}
.pokemon-container:hover{
	transform: rotate(5deg);
}
.pokemon-container:hover img{
	filter: grayscale(100%);
}
.pokemon-info-container{
	width: 100%;
	display: flex;
  height: 140px;
  align-items: center;
  justify-content: space-around;
}
.title{
	width: 100%;
  height: 60px;
  background:#bca136;
  border-top-left-radius: inherit;
	color: white;
	font-weight: 300;
  display: flex;
  border-top-right-radius: inherit;
  justify-content: center;
  align-items: center;
	transition: ease-in-out 1s;
}
.pokemon-container:hover .title {
	background-color: #ebc944;
}
.pokemon-info-container img {
	transition: ease-in-out 0.5s;
	width:100px ;
	height: 100px;
	filter: drop-shadow(6px 2px 1px lightgray);
}
</style>


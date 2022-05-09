<script>
import axios from 'axios';

export default class PokemonRepository {

	constructor() {
		this.axiosService = axios.create({
			baseURL: "https://pokeapi.co/api/v2/",
		});
	}

    async getPokemonLimit(limit){
     console.log(limit)
     let querry = limit
     return this.axiosService.get(`pokemon/${querry}`)
    }

    async getPokemon(name){
        return this.axiosService.get(`pokemon/${name}/`)
    }

}
</script>
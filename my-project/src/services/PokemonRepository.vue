<script>
import axios from 'axios';

export default class PokemonRepository {

	constructor() {
		this.axiosService = axios.create({
			baseURL: "https://pokeapi.co/api/v2/",
		});
	}
    async getPokemonLimit(){
        return this.axiosService.get('pokemon/?limit=151&offset=0')
    }
    async getPokemon(name){
        return this.axiosService.get(`pokemon/${name}/`)
    }

}
</script>
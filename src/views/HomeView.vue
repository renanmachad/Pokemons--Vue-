<template>
  <main>
    <div class="w-full flex justify-center">
      <input
        type="text"
        placeholder="Enter the pokemon here"
        class="mt-10 p-2 border-blue-700 border-2"
        v-model="text"
      />
    </div>
    <div class="mt-10 p-4 flex flex-wrap justify-center">
      <div @onclick="" class="ml-4 text-2xl text-blue-700 cursor-pointer" v-for="(pokemon,idx) in filteredPokemons" :key="idx">
        {{pokemon.name}}
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";
import { reactive, toRefs,computed } from "vue";

export default {
  name: "Home",
  setup() {
    const state = reactive({
      pokemons: [],
      urlIdLookup: {},
      text:"",
      filteredPokemons:computed(()=>updatedPokemon())
    });
    function updatedPokemon() {
      if(!state.text){

      } 

      return state.pokemons.filter((pokemon)=>
        pokemon.name.includes(state.text)
      )
    }

    axios.get("https://pokeapi.co/api/v2/pokemon?offset=0").then((res) => {
      state.pokemons = res.data.results;

      console.log(res.data.results);

      state.urlIdLookup = res.data.results.reduce((acc, cur, idx) => {
        acc = { ...acc, [cur.name]: idx + 1 };
      });
    });
    return { ...toRefs(state) };
  },
};
</script>

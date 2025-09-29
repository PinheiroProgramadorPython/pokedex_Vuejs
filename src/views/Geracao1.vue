<script setup>
import { onMounted, ref } from 'vue';

let carregamento = ref(true);

let listaPokemon = ref([]);

let pesquisaPokemon = ref('')

onMounted(async ()=>{
    for(let i = 1; i <= 151; i++){
        let request = await fetch("https://pokeapi.co/api/v2/pokemon/"+i);
        let pokemon = await request.json();
        listaPokemon.value.push(pokemon)
    }
    
    carregamento.value = false
});

function filtrar(){
    return listaPokemon.value.filter(obj => obj.name.toLowerCase().includes(pesquisaPokemon.value.toLowerCase()))
}
</script>
<template>
    <div class="carregamento" v-if="carregamento">
        <img src="https://media.giphy.com/media/v1.Y2lkPWVjZjA1ZTQ3bGRvY21hZzByOW82MHc5dXplZmh6eHR1bDl4bW84NGM1MnlqcmtkdSZlcD12MV9naWZzX3NlYXJjaCZjdD1n/JGP4QOa1n8rcE1yHGQ/giphy.gif" alt="Carregando Pokemons">
    </div>
    <main class="container" v-if="!carregamento">
        <div class="row">
            <div class="col-12">
                <input type="text" placeholder="Qual Pokemon Vc esta Procurando?" class="form-control pesquisa" v-model="pesquisaPokemon">

                <p v-if="filtrar().length == 0">Nenhum Pokemon Encontrado</p>
                <p v-else-if="filtrar().length == 1">Foi Encontrado apenas 1 Pokemon</p>
                <p v-else>Foram encontrados {{ filtrar().length }} Pokemons</p>
            </div>          
        </div>
        <div class="row">
            <div class="col-12 col-sm-6 col-md-4 col-lg-3" v-for="pokemon in filtrar()">
                <div class="card" :class="pokemon.types[0].type.name">
                    <img :src="pokemon.sprites.other.home.front_default">
                    <p>{{ pokemon.name }}</p>
                </div>
            </div>
        </div>
    </main>
</template>
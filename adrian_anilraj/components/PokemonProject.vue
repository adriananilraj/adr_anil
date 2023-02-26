<template>
    <div>
        <div class="card" v-for="(p, i) in pokeDex" :key="i">
            <div class="title">{{p.name}}</div>
            <img :src="p.sprites.front_default"/>
            <div class="weight">{{p.weight}}kg</div>
            <div class="height">{{p.height}}m</div>
            <!-- <div class="moves">{{p.moves[0].move.url}}</div> -->
        </div>
    </div>
</template>

<script>
export default {
    name: 'Pokemon',
    data() {
        return {
            pokeDex: [],
            limit: 21,
        }
    },
    methods: {
      getPokemonAPI() {
        const errorObject = {
            status: false,
            data: {},
            message: "API Not Found Or Timeout"
        }
        // Fetch from API Server
        let pokeArry = [];
        //   let pokeDex = [];
        for(let i = 1; i < this.limit; i++) {
            const p = `https://pokeapi.co/api/v2/pokemon/${i}`
            pokeArry.push(fetch(p).then(res => res.json()))
        }

        Promise.all(pokeArry).then((results) => {
            results.map(p => {
                this.pokeDex.push({
                    name: p.name,
                    abilities: p.abilities,
                    height: p.height,
                    stats: p.stats,
                    types: p.types,
                    sprites: p.sprites,
                    weight: p.weight,
                    moves: p.moves,
                })
            })  
            })
            this.getPokemonMoves();
      },
      getPokemonMoves() {

        let movesArry = []
        for(let x = 1; x < this.limit; x++){
            console.log(x);
            const url = `https://pokeapi.co/api/v2/move/${x}`;
            movesArry.push(fetch(url).then((res) => console.log(res)));
        }

        // Promise.all(movesArry).then(result => {
        //     console.log(result);
        // })
      },
    },
    mounted() {
        this.getPokemonAPI();
    }
}
</script>

<style lang="css">
.card {
    border: 1px solid #222;
    padding: 10px 15px;
    margin: 10px;
    border-radius: 20px;
    width: 100%;
}
</style>
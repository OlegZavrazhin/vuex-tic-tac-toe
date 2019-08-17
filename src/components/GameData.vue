<template>

    <ol class="game-data" v-if="gameData && gameData.length > 0">
        <li v-for="game in gameData" :key="game.id">
            <p><strong>Winner: </strong><span class="game-data__winner">{{ game.winner }}</span></p>
            <p><strong>Date: </strong>{{ game.date }}</p>
            <p><strong>See details: </strong><router-link :to="`/games/${game.id}`">Link</router-link></p>
        </li>
    </ol>
    
</template>

<script>
    import { mapGetters } from 'vuex';

    export default {
        name: "GameData",
        computed: mapGetters(['gameData'])
    }
</script>

<style scoped>

    .game-data {
        margin-top: 1.5rem;
        text-align: left;
    }

    .game-data__winner {
        text-transform: capitalize;
    }

</style>
<template>
    <div class="section-film">
        <div v-for="results in store.charactersFilm.results" class="card">
            <img :src="'https://image.tmdb.org/t/p/w342/'+results.poster_path" alt="" class="copertina">
            <div class="info">
                <p>Titolo: {{ results.title }}</p>
                <p>Titolo originale: {{ results.original_title }}</p>
                <StarLevel :voto="results.vote_average" />
                <p>Voto: {{ results.vote_average }}</p>
                <!-- <p>Overview: {{ results.overview }}</p> -->
                <span v-if="results.original_language === 'en'" :class="{ 'fi fi-gb': results.original_language === 'en' }"></span>
                <span v-if="results.original_language === 'it'" :class="{ 'fi fi-it': results.original_language === 'it' }"></span>
                <span v-if="results.original_language === 'ja'" :class="{ 'fi fi-jp': results.original_language === 'ja' }"></span>
            </div>
        </div>
    </div>
    <div class="section-tv">
        <div v-for="results in store.charactersTv.results" class="card">
            <img :src="'https://image.tmdb.org/t/p/w342/'+results.poster_path" alt="" class="copertina">
            <div class="info">
                <p>Titolo: {{ results.name }}</p>
                <p>Titolo originale: {{ results.original_name }}</p>
                <StarLevel :voto="results.vote_average" />
                <p>Voto: {{ results.vote_average }}</p>
                <!-- <p>Overview: {{ results.overview }}</p> -->
                <span v-if="results.original_language === 'en'" :class="{ 'fi fi-gb': results.original_language === 'en' }"></span>
                <span v-if="results.original_language === 'it'" :class="{ 'fi fi-it': results.original_language === 'it' }"></span>
                <span v-if="results.original_language === 'ja'" :class="{ 'fi fi-jp': results.original_language === 'ja' }"></span>
            </div>
        </div>
    </div>
</template>
<script>
import store from '../store';
import StarLevel from './StarLevel.vue';
import "/node_modules/flag-icons/css/flag-icons.min.css";

export default {
    components:{
        StarLevel
    },
    data() {
        return {
            store,
        }
    }
}
</script>
<style lang="scss" scoped>

.section-film, .section-tv{
    display: flex;
    overflow-x: scroll;
    gap: 5px;
}
.card {
    display: flex;
    position: relative;
    min-width: 300px;

    .copertina{
        object-fit: cover;
        object-position: center; 
    }
    
    p, span {
        color: white;
    }
    .info{
        display: none;
        position: absolute;
        padding: 20px;
    }
}
.card:hover{
    img{
        opacity: 0.1;
    }
    .info{
        display: block;
        height: auto;
    }
}

</style>
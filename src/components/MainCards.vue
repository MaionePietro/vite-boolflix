<template>
    <div class="section-film">
        <div v-for="results in store.charactersFilm.results" class="card">
            <img :src="'https://image.tmdb.org/t/p/w342/'+results.poster_path" alt="" class="copertina">
            <div class="info">
                <div class="info_sect">
                    <h2>{{ results.title }}</h2>
                </div>
                <div class="info_sect">
                    <h3>Titolo originale</h3>
                    <p>{{ results.original_title }}</p>
                </div>
                <div class="info_sect">
                    <StarLevel :voto="results.vote_average" />
                </div>
                <div class="info_sect">
                    <span v-if="results.original_language === 'en'" :class="{ 'fi fi-gb': results.original_language === 'en' }"></span>
                    <span v-if="results.original_language === 'it'" :class="{ 'fi fi-it': results.original_language === 'it' }"></span>
                    <span v-if="results.original_language === 'ja'" :class="{ 'fi fi-jp': results.original_language === 'ja' }"></span>
                </div>
                <div class="info_sect">
                    <h3>Overview</h3>
                    <p>{{ results.overview }}</p>
                </div>
            </div>
        </div>
    </div>
    <div class="section-tv">
        <div v-for="results in store.charactersTv.results" class="card">
            <img :src="'https://image.tmdb.org/t/p/w342/'+results.poster_path" alt="" class="copertina">
            <div class="info">
                <div class="info_sect">
                    <h2>{{ results.name }}</h2>
                </div>
                <div class="info_sect">
                    <h3>Titolo originale</h3>
                    <p>{{ results.original_name }}</p>
                </div>
                <div class="info_sect">
                    <StarLevel :voto="results.vote_average" />
                </div>
                <div class="info_sect">
                    <p>Attori: {{ fetchCharacters(results.id) }}</p>
                </div>
                <div class="info_sect">
                    <span v-if="results.original_language === 'en'" :class="{ 'fi fi-gb': results.original_language === 'en' }"></span>
                    <span v-if="results.original_language === 'it'" :class="{ 'fi fi-it': results.original_language === 'it' }"></span>
                    <span v-if="results.original_language === 'ja'" :class="{ 'fi fi-jp': results.original_language === 'ja' }"></span>
                </div>
                <div class="info_sect">
                    <h3>Overview</h3>
                    <p>{{ results.overview }}</p>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import store from '../store';
import StarLevel from './StarLevel.vue';
import axios from 'axios';
import "/node_modules/flag-icons/css/flag-icons.min.css";

export default {
    components:{
        StarLevel
    },
    data() {
        return {
            store,
        }
    },
    methods:{
        fetchCharacters(id){
            let concatena =''
            const apyKey = this.store.apyKey
            axios
            .get(`https://api.themoviedb.org/3/tv/${id}/credits`,{
                params:{
                    api_key: apyKey,
                    language: 'it-IT',
                }
            }).then((res) => {
                this.store.nomi = res.data.cast.original_name
            })
            // for(const i=0; i<5; i++){
            //         console.log(this.store.nomi[i])
            //         //concatena += this.store.nomi[i];
            //     }
            // return concatena;
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
    overflow: auto;
    text-align: center;
    .info_sect{
        color: white;
        margin-bottom: 20px;
    }

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
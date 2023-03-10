<template>
    <div class="section-film">
        <div v-for="result in store.charactersFilm.results" class="card">
            <img :src="'https://image.tmdb.org/t/p/w342/'+result.poster_path" alt="" class="copertina">
            <div class="info">
                <div class="info_sect">
                    <h2>{{ result.title }}</h2>
                </div>
                <div class="info_sect">
                    <h3>Titolo originale</h3>
                    <p>{{ result.original_title }}</p>
                </div>
                <div class="info_sect">
                    <StarLevel :voto="result.vote_average" />
                </div>
                <div class="info_sect">
                    <p v-for="(actor, i) in result.actors"
                    v-show="i < 5">
                        {{ actor.name }}
                    </p>
                </div>
                <div class="info_sect">
                    <span v-if="result.original_language === 'en'" :class="{ 'fi fi-gb': result.original_language === 'en' }"></span>
                    <span v-if="result.original_language === 'it'" :class="{ 'fi fi-it': result.original_language === 'it' }"></span>
                    <span v-if="result.original_language === 'ja'" :class="{ 'fi fi-jp': result.original_language === 'ja' }"></span>
                </div>
                <div class="info_sect">
                    <h3>Overview</h3>
                    <p>{{ result.overview }}</p>
                </div>
            </div>
        </div>
    </div>
    <div class="section-tv">
        <div v-for="result in store.charactersTv.results" class="card">
            <img :src="'https://image.tmdb.org/t/p/w342/'+result.poster_path" alt="" class="copertina">
            <div class="info">
                <div class="info_sect">
                    <h2>{{ result.name }}</h2>
                </div>
                <div class="info_sect">
                    <h3>Titolo originale</h3>
                    <p>{{ result.original_name }}</p>
                </div>
                <div class="info_sect">
                    <StarLevel :voto="result.vote_average" />
                </div>
                <div class="info_sect">
                    <p v-for="(actor, i) in result.actors"
                    v-show="i < 5">
                        {{ actor.name }}
                    </p>
                </div>
                <div class="info_sect">
                    <span v-if="result.original_language === 'en'" :class="{ 'fi fi-gb': result.original_language === 'en' }"></span>
                    <span v-if="result.original_language === 'it'" :class="{ 'fi fi-it': result.original_language === 'it' }"></span>
                    <span v-if="result.original_language === 'ja'" :class="{ 'fi fi-jp': result.original_language === 'ja' }"></span>
                </div>
                <div class="info_sect">
                    <h3>Overview</h3>
                    <p>{{ result.overview }}</p>
                </div>
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
    -webkit-overflow-scrolling: touch;
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
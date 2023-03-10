<template>
    <HeaderApp @searchText="fetchCharacters" />
    <div class="main">
        <MainCards />
    </div>
</template>
<script>
import axios from 'axios';
import store from '../store';
import MainCards from './MainCards.vue';
import HeaderApp from './HeaderApp.vue';
export default {
    components: {
        MainCards,
        HeaderApp
    },
    data() {
        return {
            store
        }
    },
    methods: {
        fetchCharacters() {
            const textSearch = this.store.textSearch;
            const apyKey = this.store.apyKey
            axios
                .get('https://api.themoviedb.org/3/search/tv', {
                    params: {
                        query: textSearch,
                        api_key: apyKey,
                        language: 'it-IT',
                    }
                }).then((res) => {
                    this.store.charactersTv = res.data
                }).catch((error) => {
                    //console.log('errore serieTv: '+error)
                }),
                axios
                    .get('https://api.themoviedb.org/3/search/movie', {
                        params: {
                            query: textSearch,
                            api_key: apyKey,
                            language: 'it-IT',
                        }
                    }).then((res) => {
                        this.store.charactersFilm = res.data
                    }).catch((error) => {
                        //console.log('errore film: '+error)
                        //this.store.charactersFilm = []
                    })
        },
        fetchCharactersCastTv() {
            for (let i = 0; i < this.store.charactersTv.results.length; i++) {
                const apyKey = this.store.apyKey
                axios
                    .get(`https://api.themoviedb.org/3/tv/${this.store.charactersTv.results[i].id}/credits`, {
                        params: {
                            api_key: apyKey
                        }
                    }).then((res) => {
                        this.store.charactersTv.results[i]['actors']= res.data.cast
                    })
            }
        }
    },
    created() {
        this.fetchCharacters()
    },
    computed: {
        prova() {
            return this.store.charactersTv
        }
    },
    watch: {
        prova() {
            this.fetchCharactersCastTv()
        }
    }

}
</script>
<style lang="scss" scoped>
@use'../style/partials/_variables' as *;

.main {
    min-height: calc(100vh - 90px);
    background-color: $bg-main;
}
</style>
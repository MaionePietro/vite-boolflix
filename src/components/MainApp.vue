<template>
    <HeaderApp @searchText="fetchCharacters"/>
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
    components:{
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
            axios
            .get('https://api.themoviedb.org/3/search/tv?api_key=974f643eea3f3c14a8d3e50ae8737a52&query=mare&language=it-IT',{
                params:{
                    query: textSearch,
                    api_key: '974f643eea3f3c14a8d3e50ae8737a52',
                    language: 'it-IT',
                }
            }).then((res) => {
                //console.log('chiamata oggetto: ' + res.data[0].results[0].original_title)
                this.store.charactersTv = res.data
            }).catch((error) => {
                    console.log(error)
                    this.store.charactersFilm = []
                    this.store.charactersTv = []
            }),
            axios
            .get('https://api.themoviedb.org/3/search/movie?api_key=974f643eea3f3c14a8d3e50ae8737a52&query=ritorno+al+fut&language=it-IT',{
                params:{
                    query: textSearch,
                    api_key: '974f643eea3f3c14a8d3e50ae8737a52',
                    language: 'it-IT',
                }
            }).then((res) => {
                console.log('chiamata oggetto: ' + res.data)
                this.store.charactersFilm = res.data
            }).catch((error) => {
                    console.log(error)
                    this.store.charactersFilm = []
                    this.store.charactersTv = []
            })
        }
    },
    created() {
        this.fetchCharacters()
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
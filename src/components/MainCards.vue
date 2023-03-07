<template>
    <div v-for="results in store.characters.results"
    class="card">
        <p>{{ results.title }}</p>  
        <p>{{ results.original_title}}</p>
        <p>{{ results.original_language}}</p>
        <p>{{ results.vote_average}}</p>
    </div>
</template>
<script>
import store from '../store';
export default {
    data(){
        return{
            store
        }
    }
}
</script>
<style lang="scss" scoped>
    .card{
        display: flex;
        p{
            color: white;
        }
    }
</style>
<template>
    <div v-for="results in store.characters">
        <p>{{ character.results[1].backdrop_path }}</p>  
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
    
</style>
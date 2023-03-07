<template>
    <div v-for="results in store.characters">
        <p>{{ results[0].overview }}</p>  
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
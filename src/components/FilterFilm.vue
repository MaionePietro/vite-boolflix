<template lang="">
    <div>
        <div class="input-group">
            <input 
            type="text" placeholder="inserisci" v-model="store.textSearch"
            @keyup.enter="$event => $emit('searchText')"
            >
            <button>cerca</button>
        </div>
    </div>
</template>

<script>
import store from '../store';
export default {
    data(){
        return {
            store
        }
    }
}
</script>

<style lang="scss" scoped>
    
</style>
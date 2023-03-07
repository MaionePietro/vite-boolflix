<template>
    <div class="sidebar">
        <div class="logo">
            <h1><a href="">BoolFlix</a></h1>
        </div>
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
        return{
            store
        }
    }
}
</script>
<style lang="scss" scoped>
    @use'../style/partials/_variables' as *;
    .sidebar{
        height: 90px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 30px;
        background-color: $bg-side;
        .logo{
            color: $color-booltflix;
            font-weight: 700;
        }
    }
</style>
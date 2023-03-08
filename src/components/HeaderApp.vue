<template>
    <div class="sidebar">
        <div class="logo">
            <a href="">
                <img src="/img/BoolFlix.png" alt="">
            </a>
        </div>
        <div class="input-container">
            <button class="button-input" @click="$event => $emit('searchText')">
                <font-awesome-icon icon="fa-solid fa-magnifying-glass" class="icon" />            
            </button>
            <input class="input" type="text" placeholder="Titoli, persone e generi" v-model="store.textSearch">
        </div>
    </div>
</template>
<script>

import store from '../store';
// import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
export default {
    // components:{
    //     FontAwesomeIcon,
    // },
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
            width: 10%;
        }
        .input-container{
            display: flex;
            padding: 10px;
            width: 40px;
            gap: 10px;
            transition: width 3s;
            
            .input{
                color: white;
                display: none;
                background: none;
                border: none;
                font-size: 10px;
            }
            .button-input{
                background: none;
                border: none;
                .icon{
                    color: white;
                    font-size: 20px;
                }
            }
        }
        .input-container:hover{
            width: 200px;
            border: solid 1px white;
            border-radius: 20px;
            transition: width 3s;
            .input{
                display: block;
                overflow: auto;
                border: none;
            }
        }
        span{
            color: white;
        }
    }
</style>
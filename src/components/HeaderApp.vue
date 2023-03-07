<template>
    <div class="sidebar">
        <div class="logo">
            <h1><a href="">BoolFlix</a></h1>
        </div>
        <FilterFilm />
    </div>
</template>
<script>
import FilterFilm from './FilterFilm.vue';
export default {
    components:{
        FilterFilm
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
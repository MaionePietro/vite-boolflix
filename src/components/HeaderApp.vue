<template>
    <div class="sidebar">
        <div class="logo">
            <h1><a href="">BoolFlix</a></h1>
        </div>
        <FilterCards />
    </div>
</template>
<script>
import FilterCards from './FilterCards.vue';
export default {
    components:{
        FilterCards
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
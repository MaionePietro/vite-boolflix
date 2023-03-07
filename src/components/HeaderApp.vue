<template>
    <div class="sidebar">
        <div class="logo">
            <h1><a href="">BoolFlix</a></h1>
        </div>
        <div class="search">
            <input type="text">
            <button>cerca</button>
        </div>
    </div>
</template>
<script>
export default {
    
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
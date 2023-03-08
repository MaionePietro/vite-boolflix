<template>
    <div>
        <font-awesome-icon icon="fa-solid fa-star" :class="{ 'gold' : voto > 2 }" />
        <font-awesome-icon icon="fa-solid fa-star" :class="{ 'gold' : voto > 4 }"/>
        <font-awesome-icon icon="fa-solid fa-star" :class="{ 'gold' : voto > 6 }"/>
        <font-awesome-icon icon="fa-solid fa-star" :class="{ 'gold' : voto > 8 }"/>
        <font-awesome-icon icon="fa-solid fa-star" :class="{ 'gold' : voto > 10 }"/>
    </div>
</template>
<script>
export default {
    props: {
        voto: {
            type: Number,
            required: true
        }
    }
}
</script>
<style lang="scss">
.gold{
    color: gold;
}
    
</style>
<template>
    <div v-for="results in store.characters.results" class="card">
        <p v-if="results.original_language === 'en'">ciao</p>
        <p>{{ results.title }}</p>
        <p>{{ results.original_title }}</p>
        <p>{{ results.original_language }}</p>
        <p>{{ results.vote_average }}</p>
        <span v-if="results.original_language === 'en'"
            :class="{ 'fi fi-gb flag': results.original_language === 'en' }"></span>
        <span v-if="results.original_language === 'it'"
            :class="{ 'fi fi-it flag': results.original_language === 'it' }"></span>
        <span v-if="results.original_language === 'ja'"
            :class="{ 'fi fi-jp flag': results.original_language === 'ja' }"></span>
    </div>
    <FlagConver />
</template>
<script>
import store from '../store';
import "/node_modules/flag-icons/css/flag-icons.min.css";

export default {
    data() {
        return {
            store,
        }
    }
}
</script>
<style lang="scss" scoped>
.card {
    display: flex;

    p {
        color: white;
    }
}

.flag {
    background-size: contain;
    background-position: 50%;
    background-repeat: no-repeat;
}
</style>
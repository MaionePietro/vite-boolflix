<template>
    <div v-for="results in store.charactersFilm.results" class="card">
        <p>{{ results.title }}</p>
        <p>{{ results.original_title }}</p>
        <p>{{ results.vote_average }}</p>
        <span v-if="results.original_language === 'en'"
            :class="{ 'fi fi-gb': results.original_language === 'en' }"></span>
        <span v-if="results.original_language === 'it'"
            :class="{ 'fi fi-it': results.original_language === 'it' }"></span>
        <span v-if="results.original_language === 'ja'"
            :class="{ 'fi fi-jp': results.original_language === 'ja' }"></span>
    </div>
    <div v-for="results in store.charactersTv.results" class="card">
        <p>{{ results.name }}</p>
        <p>{{ results.original_name }}</p>
        <p>{{ results.vote_average }}</p>
        <span v-if="results.original_language === 'en'"
            :class="{ 'fi fi-gb': results.original_language === 'en' }"></span>
        <span v-if="results.original_language === 'it'"
            :class="{ 'fi fi-it': results.original_language === 'it' }"></span>
        <span v-if="results.original_language === 'ja'"
            :class="{ 'fi fi-jp': results.original_language === 'ja' }"></span>
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

</style>
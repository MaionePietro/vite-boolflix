<script>
import HeaderApp from './components/HeaderApp.vue';
import MainApp from './components/MainApp.vue';
export default{
  components:{
    HeaderApp,
    MainApp
  }
}
</script>

<template>
  <HeaderApp />
  <MainApp />
</template>

<style lang="scss">
@use'./style/general.scss';

</style>

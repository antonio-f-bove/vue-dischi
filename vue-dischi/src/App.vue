<template>
  <div id="app">
    <the-header />
    <loader-dots v-if="discoteca.length !== 10"/>
    <the-main v-else :albums="discoteca"/>
  </div>
</template>

<script>
import axios from 'axios'
import TheHeader from './components/TheHeader.vue'
import TheMain from './components/TheMain.vue'
import LoaderDots from './components/LoaderDots.vue'

export default {
  name: "App",
  components: {
    TheMain,
    TheHeader,
    LoaderDots
  },
  data() {
    return {
      discoteca: [],
    }
  },
  mounted() {
    axios
    .get('https://flynn.boolean.careers/exercises/api/array/music')
    .then((result) => {
      this.discoteca = result.data.response;
    });
  }
};
</script>

<style lang="scss">
@import './style/main.scss';
</style>

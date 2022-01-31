<template>
  <div id="app">
    <the-header />
    <the-main :albums="discoteca"/>
  </div>
</template>

<script>
import axios from 'axios'
import TheHeader from './components/TheHeader.vue'
import TheMain from './components/TheMain.vue'

export default {
  name: "App",
  components: {
    TheMain,
    TheHeader
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

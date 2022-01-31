<template>
  <div id="app">
    <the-main :albums="discoteca"/>
  </div>
</template>

<script>
import axios from 'axios'

import TheMain from './components/TheMain.vue'

export default {
  name: "App",
  components: {
    TheMain
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

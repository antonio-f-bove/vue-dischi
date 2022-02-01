<template>
  <div id="app">
    <the-header />
    <select-genres :genres="genresList" @select="filterAlbums"/>
    <loader-dots v-if="discoteca.length !== 10" />
    <the-main v-else :albums="discotecaFiltered" />
  </div>
</template>

<script>
import axios from "axios";
import TheHeader from "./components/TheHeader.vue";
import TheMain from "./components/TheMain.vue";
import LoaderDots from "./components/LoaderDots.vue";
import SelectGenres from "./components/SelectGenres.vue";

export default {
  name: "App",
  components: {
    TheMain,
    TheHeader,
    LoaderDots,
    SelectGenres,
  },
  data() {
    return {
      // lista principale
      discoteca: [],
      // lista filtrata con la select, che verrà effettivamente stampata
      discotecaFiltered: [],
      genresList: [],
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((result) => {
        this.discoteca = result.data.response;
        this.discotecaFiltered = this.discoteca;
        this.genresList = this.getGenresList(this.discoteca);
      });
  },
  methods: {
    getGenresList(discsArray) {
      const genres = ["All genres"];

      discsArray.forEach((disc) => {
        if (!genres.includes(disc.genre)) {
          genres.push(disc.genre);
        }
      });

      return genres;
    },
    filterAlbums (option) {
      this.discotecaFiltered = this.discoteca.filter((album) => {
        return album.genre === option || option === 'All genres'
      })
    }
  },
};
</script>

<style lang="scss">
@import "./style/main.scss";
</style>

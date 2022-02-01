<template>
  <div id="app">
    <the-header />
    <select-genre :genres="genresList" @select="filterAlbums"/>
    <select-artist :artists="artistsList" @select="filterAlbums" />
    <loader-dots v-if="discoteca.length !== 10" />
    <the-main v-else :albums="discotecaFiltered" />
  </div>
</template>

<script>
import axios from "axios";
import TheHeader from "./components/TheHeader.vue";
import TheMain from "./components/TheMain.vue";
import LoaderDots from "./components/LoaderDots.vue";
import SelectGenre from "./components/SelectGenre.vue";
import SelectArtist from './components/SelectArtist.vue';

export default {
  name: "App",
  components: {
    TheMain,
    TheHeader,
    LoaderDots,
    SelectGenre,
    SelectArtist,
  },
  data() {
    return {
      // lista principale
      discoteca: [],
      // lista filtrata con la select, che verrà effettivamente stampata
      discotecaFiltered: [],
      genresList: [],
      artistsList: [],
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((result) => {
        this.discoteca = result.data.response;
        this.discotecaFiltered = this.discoteca;
        this.genresList = this.getGenresList(this.discoteca);
        this.artistsList = this.getArtistsList(this.discoteca);
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
    getArtistsList(discsArray) {
      const artists = ["All artists"];

      discsArray.forEach((disc) => {
        if (!artists.includes(disc.author)) {
          artists.push(disc.author);
        }
      });

      return artists;
    },
    filterAlbums (option, filter) {
      if (filter === 'genre') {
        this.discotecaFiltered = this.discoteca.filter((album) => {
          return album.genre === option || option === 'All genres'
        })
      }

      if (filter === 'artist') {
        this.discotecaFiltered = this.discoteca.filter((album) => {
          return album.author === option || option === 'All artists'
        })
      }
    }
  },
};
</script>

<style lang="scss">
@import "./style/main.scss";
</style>

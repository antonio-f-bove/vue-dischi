<template>
  <select v-model="selectedGenre" @change="$emit('select', selectedGenre, 'genre')"
  >
    <option v-for="genre in genres" :key="genre" :value="genre">
      {{ genre }}
    </option>
  </select>
</template>

<script>
export default {
  props: {
    genres: Array,
  },
  data() {
    return {
      selectedGenre: 'All genres',
    }
  }
};
</script>

<style lang="scss" scoped></style>

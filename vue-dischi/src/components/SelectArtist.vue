<template>
  <select v-model="selectedArtist" @change="$emit('select', selectedArtist, 'artist')"
  >
    <option v-for="artist in artists" :key="artist" :value="artist">
      {{ artist }}
    </option>
  </select>
</template>

<script>
export default {
  props: {
    artists: Array,
  },
  data() {
    return {
      selectedArtist: 'All artists',
    }
  }
};
</script>

<style lang="scss" scoped></style>

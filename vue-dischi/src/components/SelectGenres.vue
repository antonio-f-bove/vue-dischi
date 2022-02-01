<template>
  <select @change="$emit('change', $event.target.value)"
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
    genre: String,
  },
  data() {
    return {
    }
  }
};
</script>

<style lang="scss" scoped></style>

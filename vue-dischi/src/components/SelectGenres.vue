<template>
  <select v-model="">
    <option v-for="genre in genres" 
    :key="genre"
    :value="genre"
    >
      {{ genre }}
    </option>
  </select>
</template>

<script>
export default {
  props: {
    genres: Array
  }
}
</script>

<style lang="scss" scoped>

</style>
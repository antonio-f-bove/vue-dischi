<template>
  <main>
    <div class="container-custom">
      <div class="row row-cols-5">
        <card-box v-for="(album, index) in albums" 
        :key="index" 
        :album="album" 
        class="col" 
        />
      </div>
    </div>
  </main>
</template>

<script>
import CardBox from './CardBox.vue'

export default {
  components: {
    CardBox,
  },
  props: {
    albums: Array
  }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

main {
  background-color: $dark-blue;

  .container-custom {
    width: 1000px;
    margin: 0 auto;
  }
}
</style>
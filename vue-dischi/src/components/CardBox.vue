<template>
  <div class="wrapper px-3">
    <div class="card p-3 mb-3">
      <div class="img-container mb-3">
        <img class="img-fluid" :src="album.poster">
      </div>
      <div class="text-container text-center">
        <h6 class="album text-white mb-3">{{ album.title.toUpperCase() }}</h6>
        <div class="details-box text-white-50">
          <p>{{ album.author }}</p>
          <p>{{ album.year }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    album: Object
  }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

.wrapper{

  .card {
    background-color: $light-blue;
    height: 300px;

    .details-box {
      // height: 120px;

      p {
        line-height: 1.2em;
        margin-bottom: 0;
      }
    }
  }
}
</style>
<template>
  <article class="film">
    <h2>{{film.title[0].value}}</h2>
    <img :src="'https://statics.ocs.fr' + film.imageurl">
    <!--      <a :href="'https://go.ocs.fr/details/' + item.detaillink">detail</a>-->
    <p>{{film.subtitle}}</p>
    <p>{{film.detaillink}}</p>
  </article>
</template>

<script>
export default {
  name: "Film",
  props: {
    film: {
      type: Object,
      required: true
    },
    standalone: {
      // if true, this component process the add to cart otherwise fire an event that another component will read to process the add to cart
      type: Boolean,
      default: true
    }
  },
}
</script>

<style scoped>
  h2 {
    font-size: 1.3rem;
    font-weight: bold;
  }
  .film {
    margin-bottom: 2rem;
  }
</style>

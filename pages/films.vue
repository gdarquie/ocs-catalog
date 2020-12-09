<template>
  <div class="container">
    <h1>OCS Catalog - New Films this week</h1>
    <div class="columns is-desktop is-multiline">
      <div v-for="item in result.contents" :key="item.id">
        <article class="column">
          <Film :film="item" />
        </article>
      </div>
    </div>
  </div>
</template>

<script>
import Film from "@/components/Film";
export default {
  name: "films",
  components: {Film},
  async asyncData({ $axios }) {
    let result = null
    await $axios
      .get(`https://api.ocs.fr/web/v2/rubriques/films?sort=new`)
      .then((res) => {
        result = res.data
      })

    return {
      result
    }
  }
}

</script>

<style scoped>
  h1 {
    font-size: 3rem;
    text-align: center;
    margin-bottom: 3rem;
  }
</style>

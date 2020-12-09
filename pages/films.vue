<template>
  <div class="container is-fullhd">
    <div v-for="item in result.contents" :key="item.id">
      <Film :film="item" />
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

</style>

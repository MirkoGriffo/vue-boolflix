<template>
  <main>
    <section v-show="films.length" class="films">
      <h2>Film</h2>
      <Card v-for="film in films" :key="film.id" :info="film" />
    </section>
    <section v-show="series.length" class="serie">
      <h2>Serie TV</h2>
      <Card v-for="serie in series" :key="serie.id" :info="serie" />
    </section>
  </main>
</template>

<script>
import Card from "@/components/Card.vue";

export default {
  name: "Main",
  components: {
    Card,
  },
  props: {
    films: Array,
    series: Array,
  },

  data() {
    return {};
  },
};
</script>

<style scoped>
</style>
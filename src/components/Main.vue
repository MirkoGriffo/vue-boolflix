<template>
  <main>
    <div class="container">
      <section v-show="films.length" class="films">
        <h2>Film</h2>
        <div class="card">
          <Card v-for="film in films" :key="film.id" :info="film" />
        </div>
      </section>

      <section v-show="series.length" class="serie">
        <h2>Serie TV</h2>
        <div class="card">
          <Card v-for="serie in series" :key="serie.id" :info="serie" />
        </div>
      </section>
    </div>
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
};
</script>

<style scoped>
.container {
  width: 1500px;
  margin: 0 auto;
}
main {
  height: 100%;
  background-color: gray;
}
.card {
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  justify-content: start;
  align-items: auto;
  align-content: start;
}
h2 {
  text-align: center;
  font-size: 50px;
  color: white;
  text-transform: uppercase;
  padding: 50px;
}
</style>
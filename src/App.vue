<template>
  <div id="app">
    <Header @performSearch="cercaFilm" />
    <Main :films="listaFilm" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
import Main from "@/components/Main.vue";
export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      listaFilm: [],
      filmAPI: "https://api.themoviedb.org/3/search/movie",
      trendAPI: "https://api.themoviedb.org/3/trending/all/week",
    };
  },
  created() {
    axios
      .get(this.trendAPI, {
        params: {
          api_key: "36e4892e17d62c22400a959373f6e799",
        },
      })
      .then((res) => {
        this.listaFilm = res.data.results;
      })
      .catch((err) => {
        console.log(err);
      });
  },
  methods: {
    cercaFilm(text) {
      axios
        .get(this.filmAPI, {
          params: {
            api_key: "36e4892e17d62c22400a959373f6e799",
            query: text,
            language: "it-IT",
          },
        })
        .then((res) => {
          this.listaFilm = res.data.results;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style lang="scss">
#app {
}
</style>

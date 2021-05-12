<template>
  <div id="app">
    <Header @performSearch="cercaFilm" />
    <Main :films="listaFilm" :series="listaSerie" />
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
      listaSerie: [],
      apiUrl: "https://api.themoviedb.org/3/search/",
      apiKey: "36e4892e17d62c22400a959373f6e799",
      trendAPI: "https://api.themoviedb.org/3/trending/all/week",
    };
  },
  created() {
    axios
      .get(this.trendAPI, {
        params: {
          api_key: this.apiKey,
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
      if (text !== " ") {
        const apiParams = {
          api_key: this.apiKey,
          query: text,
          language: "it-IT",
        };
        //Film
        axios
          .get(this.apiUrl + "movie", {
            params: apiParams,
          })
          .then((res) => {
            this.listaFilm = res.data.results;
          })
          .catch((err) => {
            console.log(err);
          });

        //Serie tv
        axios
          .get(this.apiUrl + "tv", {
            params: apiParams,
          })
          .then((res) => {
            this.listaSerie = res.data.results;
          })
          .catch((err) => {
            console.log(err);
          });
      }
    },
  },
};
</script>

<style lang="scss">
#app {
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
</style>

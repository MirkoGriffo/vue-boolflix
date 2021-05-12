<template>
  <div class="card">
    <img
      v-if="info.poster_path !== null"
      class="poster"
      :src="`https://image.tmdb.org/t/p/w342/${info.poster_path}`"
      alt=""
    />
    <img v-else class="poster" src="@/assets/img/not-found.png" alt="" />
    <div class="overlay">
      <ul>
        <li>
          <strong>Titolo:</strong>
          {{ info.title ? info.title : info.name }}
        </li>
        <li>
          <strong>Titolo Originale:</strong>
          {{ info.original_title ? info.original_title : info.original_name }}
        </li>

        <li>
          <img
            class="bandiera"
            v-if="isFlag(info.original_language)"
            :src="require(`@/assets/img/${info.original_language}.png`)"
            alt=""
          />
        </li>
        <li>
          <strong>Voto: </strong>
          <span
            class="stella"
            v-for="(stella, index) in convertiNumero(info.vote_average)"
            :key="index"
          >
            <i class="fa fa-star"></i>
          </span>
          <span
            v-for="(stella, index) in 5 - convertiNumero(info.vote_average)"
            :key="index"
          >
            <i class="far fa-star"></i>
          </span>
        </li>
        <li>
          <strong>Descrizione: </strong>
          {{ info.overview }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["info"],
  data() {
    return {
      flagsImg: ["it", "en"],
    };
  },
  methods: {
    isFlag(lang) {
      return this.flagsImg.includes(lang);
    },
    convertiNumero(voto) {
      return Math.round(voto / 2);
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  color: white;
}
ul li {
  margin: 25px;
}
.card {
  position: relative;
  width: 300px;
  margin: 25px;
}
.poster {
  width: 100%;
  height: 100%;
}
.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.8);
  color: #fff;
  opacity: 0;
  transition: 0.2s ease;
  overflow: auto;
}

.overlay:hover {
  opacity: 1;
}
.bandiera {
  width: 25%;
}
.stella {
  color: yellow;
}
strong {
  color: #4da6ff;
}
</style>

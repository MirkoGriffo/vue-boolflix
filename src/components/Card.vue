<template>
  <div class="card">
    <img
      class="poster"
      :src="`https://image.tmdb.org/t/p/w342/${info.poster_path}`"
      alt=""
    />
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
          v-if="isFlag(info.original_language)"
          :src="require(`@/assets/img/${info.original_language}.png`)"
          alt=""
        />
      </li>
      <li>
        <strong>Voto: </strong>
        <span
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
    </ul>
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
</style>

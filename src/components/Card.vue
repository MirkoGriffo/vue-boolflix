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
        {{ info.title }}
      </li>
      <li>
        <strong>Titolo Originale:</strong>
        {{ info.original_title }}
      </li>

      <li>
        <img
          v-if="isFlag(info.original_language)"
          :src="require(`@/assets/img/${info.original_language}.png`)"
          alt=""
        />
      </li>
      <li>
        <strong>Voto:</strong>
        {{ info.vote_average }}
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
  },
};
</script>

<style scoped>
</style>

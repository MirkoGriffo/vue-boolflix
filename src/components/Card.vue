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
        <strong>Lingua Originale:</strong>
        {{ info.original_language }}
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
    return {};
  },
};
</script>

<style scoped>
</style>

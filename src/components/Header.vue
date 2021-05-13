<template>
  <header>
    <div class="container">
      <img class="logo" src="@/assets/img/mirkoflix.png" alt="logo" />
      <form>
        <div><input type="text" v-model.trim="searchText" /></div>
        <div class="btn">
          <button
            type="submit"
            @click.prevent="$emit('performSearch', searchText)"
          >
            Cerca
          </button>
        </div>
      </form>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      searchText: "",
    };
  },
};
</script>

<style scoped>
.container {
  width: 1500px;
  margin: 0 auto;
}

.logo {
  position: relative;
  top: 25px;
}
header {
  height: 130px;
  width: 100%;
  background-color: black;
  position: fixed;
  z-index: 1;
}
form {
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  justify-content: flex-end;
  position: relative;
  bottom: 30px;
}
form input {
  width: 300px;
  height: 25px;
  border: none;
  background-color: black;
  border-bottom: 1px solid red;
  color: white;
}
form button {
  margin-left: 20px;
  background-color: black;
  color: white;
  font-size: 25px;
  border: none;
  cursor: pointer;
}
</style>
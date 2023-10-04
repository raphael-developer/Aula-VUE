<template>
  <main class="main">
    <h1>{{ msg }}</h1>
    <ul>
      <li v-for="movie in movies" :key="movie.id">
        ➡️ {{ movie.title }}
      </li>
    </ul>
  </main>
</template>

<script>
import movieService from "@/services/movieService";

export default {
  name: "TheMain",
  props: {
    msg: String,
  },

  data() {
    return {
      movies: [],
    };
  },

  async mounted() {
    try {
      this.movies = await movieService.getMovies();
    } catch (error) {
      console.log(error);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

main.main {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
}

h3 {
  margin: 40px 0 0;
}

ul {
  text-align: start;
  list-style-type: none;
  padding: 0;
}

ul li {
  padding: 5px;
}
</style>

<template>
  <div>
    <Header :movieData="MovieData" />
    <MovieList :movieData="MovieData" />
    <Footer />
  </div>
</template>

<script>
import Header from "../../components/organisms/Header.vue";
import MovieList from "../../components/organisms/MovieList.vue";
import Footer from "../../components/organisms/Footer.vue";
import MovieData from "../../assets/json/movie.json";
export default {
  components: { Header, MovieList, Footer },
  name: "movie",
  data() {
    return { MovieData: MovieData };
  },
};
</script>

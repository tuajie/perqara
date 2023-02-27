<template>
  <div>
    <Header :movieData="MovieData" />
    <MovieDetail :movieData="MovieData" />
    <Footer />
  </div>
</template>

<script>
import Header from "../../components/organisms/Header.vue";
import MovieDetail from "../../components/organisms/MovieDetail.vue";
import Footer from "../../components/organisms/Footer.vue";
import MovieData from "../../assets/json/movie.json";

export default {
  components: { Header, MovieDetail, Footer },
  name: "detail",
  data() {
    return { MovieData: MovieData };
  },
};
</script>

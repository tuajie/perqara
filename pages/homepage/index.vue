<template>
  <div>
    <Header :movieData="MovieData" />
    <Carousel :movieData="MovieData" />
    <List :movieData="MovieData" />
    <Footer />
  </div>
</template>

<script>
import Header from "../../components/organisms/Header.vue";
import Carousel from "../../components/organisms/Carousel.vue";
import List from "../../components/organisms/List.vue";
import Footer from "../../components/organisms/Footer.vue";
import MovieData from "../../assets/json/movie.json";

export default {
  components: { Header, Carousel, List, Footer, MovieData },
  name: "mainpage",
  data() {
    return { MovieData: MovieData };
  },
};
</script>

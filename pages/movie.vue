<template>
  <div>
    <Header />
    <Movie />
    <Footer />
  </div>
</template>

<script>
import Header from "../components/organisms/Header.vue";
import Movie from "../components/organisms/Movie.vue";
import Footer from "../components/organisms/Footer.vue";
export default {
  components: { Header, Movie, Footer },
  name: "Movie",
};
</script>

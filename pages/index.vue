<template>
  <div>
    <Header />
    <Carousel />
    <List />
    <Footer />
  </div>
</template>

<script>
import Header from "../components/organisms/Header.vue";
import Carousel from "../components/organisms/Carousel.vue";
import List from "../components/organisms/List.vue";
import Footer from "../components/organisms/Footer.vue";
export default {
  components: { Header, Carousel, List, Footer },
  name: "Mainpage",
};
</script>

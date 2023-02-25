<template>
  <div>
    <Header />
    <Detail />
    <Footer />
  </div>
</template>

<script>
import Header from "../components/organisms/Header.vue";
import Detail from "../components/organisms/Detail.vue";
import Footer from "../components/organisms/Footer.vue";
export default {
  components: { Header, Detail, Footer },
  name: "Detail",
};
</script>

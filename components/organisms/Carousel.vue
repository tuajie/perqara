<template>
  <div class="bg-carousel min-35em">
    <div class="relative-container">
      <VueSlickCarousel v-bind="settings" class="pt-10 pb-10">
        <div
          class="box-movie"
          v-for="movie in movieData.slice(0, 3)"
          :key="movie.id"
        >
          <nuxt-link :to="`/detail?imdbID=${movie.imdbID}`">
            <div class="movie-image">
              <img :src="`${movie.Poster}`" />
            </div>
            <div class="movie-info p-8">
              <h3>
                <img
                  src="~/assets/images/Star.svg"
                  width="16"
                  class="mt-1 mr-2"
                /><span>{{ movie.imdbRating }}</span>
              </h3>
              <h4>{{ movie.Title }}</h4>
              <h5 class="pt-2 pb-2">
                <span>{{ movie.Year }} </span>
                <div class="dot mt-2 ml-1 mr-1"></div>
                <span> {{ movie.Genre }} </span>
              </h5>
              <p>
                {{ movie.Plot }}
              </p>
            </div>
          </nuxt-link>
        </div>
      </VueSlickCarousel>
    </div>
  </div>
</template>

<script>
import VueSlickCarousel from "vue-slick-carousel";
import "vue-slick-carousel/dist/vue-slick-carousel.css";
// optional style for arrows & dots
import "vue-slick-carousel/dist/vue-slick-carousel-theme.css";
export default {
  name: "Carousel",
  props: {
    movieData: {
      type: Array,
      require: true,
    },
  },
  data() {
    return {
      settings: {
        centerMode: true,
        centerPadding: "20px",
        focusOnSelect: true,
        infinite: true,
        slidesToShow: 2.2,
        speed: 500,
        dots: true,
        arrows: false,
      },
    };
  },

  components: { VueSlickCarousel },
};
</script>

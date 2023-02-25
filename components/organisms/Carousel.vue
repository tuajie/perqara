<template>
  <div class="bg-carousel">
    <VueSlickCarousel v-bind="settings" class="pt-10 pb-10">
      <div class="box-movie">
        <div class="movie-image">
          <img
            src="https://m.media-amazon.com/images/M/MV5BZWI3ZThmYzUtNDJhOC00ZWY4LThiNmMtZDgxNjE3Yzk4NDU1XkEyXkFqcGdeQXVyNTk5Nzg1NjQ@._V1_SX300.jpg"
          />
        </div>
        <div class="movie-info p-8">
          <h3>
            <img
              src="~/assets/images/Star.svg"
              width="16"
              class="mt-1 mr-2"
            /><span>7.3</span>
          </h3>
          <h4>Space Sweepers</h4>
          <h5 class="pt-2 pb-2">
            <span>2021 </span>
            <div class="dot mt-2 ml-1 mr-1"></div>
            <span> Sci-Fi </span>
          </h5>
          <p>
            A documentary about World War I with never-before-seen footage to
            commemorate the centennial of the end of the war.
          </p>
        </div>
      </div>
      <div class="box-movie">
        <div class="movie-image">
          <img
            src="https://m.media-amazon.com/images/M/MV5BZWI3ZThmYzUtNDJhOC00ZWY4LThiNmMtZDgxNjE3Yzk4NDU1XkEyXkFqcGdeQXVyNTk5Nzg1NjQ@._V1_SX300.jpg"
          />
        </div>
        <div class="movie-info p-8">
          <h3>
            <img
              src="~/assets/images/Star.svg"
              width="16"
              class="mt-1 mr-2"
            /><span>7.3</span>
          </h3>
          <h4>Space Sweepers</h4>
          <h5 class="pt-2 pb-2">
            <span>2021 </span>
            <div class="dot mt-2 ml-1 mr-1"></div>
            <span> Sci-Fi </span>
          </h5>
          <p>
            A documentary about World War I with never-before-seen footage to
            commemorate the centennial of the end of the war.
          </p>
        </div>
      </div>
      <div class="box-movie">
        <div class="movie-image">
          <img
            src="https://m.media-amazon.com/images/M/MV5BZWI3ZThmYzUtNDJhOC00ZWY4LThiNmMtZDgxNjE3Yzk4NDU1XkEyXkFqcGdeQXVyNTk5Nzg1NjQ@._V1_SX300.jpg"
          />
        </div>
        <div class="movie-info p-8">
          <h3>
            <img
              src="~/assets/images/Star.svg"
              width="16"
              class="mt-1 mr-2"
            /><span>7.3</span>
          </h3>
          <h4>Space Sweepers</h4>
          <h5 class="pt-2 pb-2">
            <span>2021 </span>
            <div class="dot mt-2 ml-1 mr-1"></div>
            <span> Sci-Fi </span>
          </h5>
          <p>
            A documentary about World War I with never-before-seen footage to
            commemorate the centennial of the end of the war.
          </p>
        </div>
      </div>
    </VueSlickCarousel>
  </div>
</template>

<script>
import VueSlickCarousel from "vue-slick-carousel";
import "vue-slick-carousel/dist/vue-slick-carousel.css";
// optional style for arrows & dots
import "vue-slick-carousel/dist/vue-slick-carousel-theme.css";
export default {
  name: "Carousel",
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
        arrows: true,
      },
    };
  },
  components: { VueSlickCarousel },
};
</script>

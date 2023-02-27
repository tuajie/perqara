<template>
  <div
    class="bg-black card-movie"
    @mouseover="mouseOver"
    @mouseleave="mouseLeave"
  >
    <nuxt-link :to="`/detail?imdbID=${movieDetail.imdbID}`">
      <div class="flex flex-row-reverse">
        <span class="rate pr-2 pl-2">{{ movieDetail.imdbRating }}</span>
      </div>
      <div v-show="upHere" class="hover-abs">
        <div class="hover grid grid-cols-1 content-center w-full">
          <h3 class="mb-4">
            <img
              src="~/assets/images/Star.svg"
              width="24"
              class="mt-2 mr-1"
            /><span>{{ movieDetail.imdbRating }}</span>
          </h3>
          <h4 class="mb-4 mt-2">{{ movieDetail.Genre }}</h4>
          <button class="text-white py-0 px-2 rounded-full mt-4">view</button>
        </div>
      </div>
      <img
        class="image-card"
        :src="`${movieDetail.Poster}`"
        :alt="`${movieDetail.Title}`"
      />
    </nuxt-link>

    <div class="pt-2 pb-2">
      <nuxt-link :to="`/detail?imdbID=${movieDetail.imdbID}`">
        <h5
          class="mb-1 text-1xl font-bold tracking-tight text-gray-900 dark:text-white"
        >
          {{ movieDetail.Title }}
        </h5>
        <p class="mb-1 font-normal text-gray-700 dark:text-gray-400">
          {{ movieDetail.Year }}
        </p>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    movie: {
      type: Object,
      require: true,
    },
  },

  data() {
    return {
      upHere: false,
      movieDetail: this.movie,
    };
  },
  methods: {
    mouseOver() {
      this.upHere = true;
    },
    mouseLeave() {
      this.upHere = false;
    },
  },
};
</script>

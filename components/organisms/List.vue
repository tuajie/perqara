<template>
  <div class="mt-2 pt-2 pb-8 relative-container">
    <div class="container mx-auto list-title flex justify-between">
      <div>
        <div class="stroke mb-2"></div>
        <h2>Discover Movies</h2>
      </div>

      <div class="">
        <div class="flex justify-end">
          <button
            type="button"
            class="inline-flex w-32 justify-center bg-red px-4 py-1 text-sm font-small text-white shadow-sm rounded-full mr-2"
            aria-expanded="true"
            aria-haspopup="true"
            @click="openDropDown"
          >
            Popularity
          </button>
          <button
            type="button"
            class="inline-flex w-full justify-center bg-carousel px-4 py-1 text-sm font-small text-white shadow-sm rounded-full"
            aria-expanded="true"
            aria-haspopup="true"
          >
            {{ filter }}
          </button>
        </div>
        <div
          class="absolute z-10 mt-2 w-56 origin-top-right rounded-md bg-white shadow-lg"
          role="menu"
          aria-orientation="vertical"
          aria-labelledby="menu-button"
          tabindex="-1"
          v-show="dropDown"
        >
          <div v-for="filter in listFilter" :key="filter">
            <div class="py-1" role="none">
              <div
                class="text-gray-700 block px-4 py-1 text-sm cursor-pointer"
                role="menuitem"
                @click="setFilter(filter)"
              >
                {{ filter }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div v-if="!isSort" class="container mx-auto grid grid-cols-5 gap-8 pt-8">
      <div v-for="movie in movieData" :key="movie.id">
        <Card :movie="movie" />
      </div>
    </div>
    <div v-else class="container mx-auto grid grid-cols-5 gap-8 pt-8">
      <div v-for="movie in dataSort" :key="movie.id">
        <Card :movie="movie" />
      </div>
    </div>
  </div>
</template>

<script>
import Card from "../molecules/Card.vue";
export default {
  name: "List",
  components: { Card },
  props: {
    movieData: {
      type: Array,
      require: true,
    },
  },

  data() {
    return {
      dropDown: false,
      filter: "Popularity Ascending",
      isSort: false,
      dataSort: [],
      listFilter: [
        "Popularity Ascending",
        "Popularity Descending",
        "Release Date Ascending",
        "Release Date Descending",
        "Rating Ascending",
        "Rating Descending",
      ],
    };
  },

  methods: {
    openDropDown() {
      this.dropDown = !this.dropDown;
    },
    setFilter(value) {
      this.isSort = true;
      this.dataSort = [];
      this.filter = value;
      this.dropDown = !this.dropDown;
      setTimeout(() => {
        if (value === "Popularity Ascending") {
          let sort = this.movieData.sort(function (a, b) {
            return a.Metascore - b.Metascore;
          });
          this.dataSort = sort;
        } else if (value === "Popularity Descending") {
          let sort = this.movieData.sort(function (a, b) {
            return b.Metascore - a.Metascore;
          });
          this.dataSort = sort;
        } else if (value === "Release Date Ascending") {
          let sort = this.movieData.sort(function (a, b) {
            return a.Year - b.Year;
          });
          this.dataSort = sort;
        } else if (value === "Release Date Descending") {
          let sort = this.movieData.sort(function (a, b) {
            return b.Year - a.Year;
          });
          this.dataSort = sort;
        } else if (value === "Rating Ascending") {
          let sort = this.movieData.sort(function (a, b) {
            return a.imdbRating - b.imdbRating;
          });
          this.dataSort = sort;
        } else if (value === "Rating Descending") {
          let sort = this.movieData.sort(function (a, b) {
            return b.imdbRating - a.imdbRating;
          });
          this.dataSort = sort;
        }
      }, 300);
    },
  },
};
</script>

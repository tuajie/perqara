<template>
  <div class="mt-8 pt-8 pb-10 relative-container">
    <div class="container mx-auto list-title flex justify-between">
      <div>
        <div class="stroke mb-2"></div>
        <h2>Movies</h2>
      </div>
    </div>
    <div class="container mx-auto flex justify-between pt-8 gap-8">
      <div class="w-1/5 bg-carousel rounded-lg sidebar">
        <h4 class="mb-4 mt-4 pt-3 pb-3 px-4 border-btm">Sort Result By</h4>
        <div class="">
          <div class="flex justify-end">
            <button
              type="button"
              class="inline-flex w-full justify-left bg-black px-4 py-1 text-sm font-small text-white shadow-sm mr-4 ml-4 py-2 rounded-sm"
              aria-expanded="true"
              aria-haspopup="true"
              @click="openDropDown"
            >
              {{ filter || "Popularity Ascending" }}
            </button>
          </div>
          <div
            class="inline-flex w-68 justify-left bg-black-true px-1 py-1 text-sm font-small text-white shadow-sm mr-4 ml-4 py-2"
            role="menu"
            aria-orientation="vertical"
            aria-labelledby="menu-button"
            tabindex="-1"
            v-if="dropDown"
          >
            <div class="py-1" role="none">
              <div v-for="filter in listFilter" :key="filter">
                <div
                  href="#"
                  class="text-white-700 block px-4 py-2 text-sm cursor-pointer"
                  role="menuitem"
                  @click="setFilter(filter)"
                >
                  {{ filter }}
                </div>
              </div>
            </div>
          </div>
        </div>
        <h4 class="mb-4 mt-4 pt-3 pb-3 px-4 border-btm-top">Genres</h4>
        <div v-for="movie in listGenre" :key="movie">
          <div class="flex justify-between item">
            <label :for="`checked-${movie}`" class="label-chck pl-4 pl-4">{{
              movie
            }}</label>
            <input
              :id="`checked-${movie}`"
              type="checkbox"
              value=""
              @click="filterCheck(movie)"
              class="w-4 h-4 text-red-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 mr-4"
            />
          </div>
        </div>
      </div>
      <div v-if="isFiltered" class="w-4/5">
        <div class="container mx-auto grid grid-cols-4 gap-8">
          <div
            v-for="movie in dataList.slice(this.start, this.end)"
            :key="movie.id"
          >
            <Card :movie="movie" />
          </div>
        </div>
        <div class="flex justify-center more">
          <button
            v-bind:class="`${
              this.end >= this.dataList.length
                ? 'bg text-white pl-2 rounded-full mt-4 w-32 opacity-50 cursor-not-allowed'
                : 'bg text-white pl-2 rounded-full mt-4 w-32'
            }`"
            @click="loadMore"
          >
            Load More
          </button>
        </div>
      </div>
      <div v-else class="w-4/5">
        <div class="container mx-auto grid grid-cols-4 gap-8">
          <div
            v-for="movie in movieData.slice(this.start, this.end)"
            :key="movie.id"
          >
            <Card :movie="movie" />
          </div>
        </div>
        <div class="flex justify-center more">
          <button
            v-bind:class="`${
              this.end >= this.movieData.length
                ? 'bg text-white pl-2 rounded-full mt-4 w-32 opacity-50 cursor-not-allowed'
                : 'bg text-white pl-2 rounded-full mt-4 w-32'
            }`"
            @click="loadMore"
          >
            Load More
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Card from "../molecules/Card.vue";
export default {
  name: "MovieList",
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
      start: 0,
      end: 8,
      disableButton: false,
      isFiltered: false,
      dataList: [],
      checkList: [],
      genre: this.$route.query.genre,
      listGenre: [
        "Action",
        "Adventure",
        "Animation",
        "Comedy",
        "Crime",
        "Documentary",
        "Drama",
        "Family",
        "Fantasy",
        "History",
        "Horror",
      ],
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

  mounted() {
    this.filterDataList();
    if (this.$route.query.genre !== undefined) {
      this.isFiltered = true;
    }
  },

  watch: {
    $route(to, from) {
      this.dataList = [];
      this.isFiltered = true;
      let queryNow = this.$route.query.genre;
      let data = this.movieData.filter((x) => x.Genre === queryNow);
      setTimeout(() => {
        this.dataList = data;
      }, 300);
    },
  },

  methods: {
    openDropDown() {
      this.dropDown = !this.dropDown;
    },
    loadMore() {
      this.end = this.end + 4;
    },
    filterDataList() {
      let data = this.movieData.filter((x) => x.Genre === this.genre);
      this.dataList = data;
    },
    filterCheck(movie) {
      this.dataList = [];
      this.isFiltered = true;
      let checkMovie = this.checkList.includes(movie);
      if (!checkMovie) {
        this.checkList.push(movie);
      } else {
        this.checkList = this.checkList.filter((data) => data !== movie);
      }
      this.$router.push("/movie");
      setTimeout(() => {
        this.dataList = this.movieData.filter((item) =>
          this.checkList.includes(item.Genre)
        );
        if (this.dataList.length === 0) {
          this.isFiltered = false;
        }
      }, 300);
    },
    setFilter(value) {
      this.filter = value;
      this.isFiltered = true;
      this.dataList = [];
      this.dropDown = !this.dropDown;
      setTimeout(() => {
        if (value === "Popularity Ascending") {
          let sort = this.movieData.sort(function (a, b) {
            return a.Metascore - b.Metascore;
          });
          this.dataList = sort;
        } else if (value === "Popularity Descending") {
          let sort = this.movieData.sort(function (a, b) {
            return b.Metascore - a.Metascore;
          });
          this.dataList = sort;
        } else if (value === "Release Date Ascending") {
          let sort = this.movieData.sort(function (a, b) {
            return a.Year - b.Year;
          });
          this.dataList = sort;
        } else if (value === "Release Date Descending") {
          let sort = this.movieData.sort(function (a, b) {
            return b.Year - a.Year;
          });
          this.dataList = sort;
        } else if (value === "Rating Ascending") {
          let sort = this.movieData.sort(function (a, b) {
            return a.imdbRating - b.imdbRating;
          });
          this.dataList = sort;
        } else if (value === "Rating Descending") {
          let sort = this.movieData.sort(function (a, b) {
            return b.imdbRating - a.imdbRating;
          });
          this.dataList = sort;
        }
      }, 300);
    },
  },
};
</script>

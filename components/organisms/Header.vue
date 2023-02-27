<template>
  <div class="bg-header p-2 absolute w-full z-10">
    <div class="flex mb-4 relative container mx-auto pt-2">
      <div class="w-1/6 flex items-center flex-shrink-0 h-10">
        <nuxt-link to="/">
          <img src="~/assets/images/MoovieTime-Logo.svg" width="100" />
        </nuxt-link>
      </div>
      <div class="w-1/2 h-10">
        <form class="block flex-none">
          <div class="mb-4">
            <autocomplete
              class="appearance-none border-gray rounded w-full py-3 px-5 bg-input text-white leading-tight focus:outline-none focus:shadow-outline pl-12"
              ref="autocomplete"
              :search="search"
              placeholder="Find movie"
              aria-label="Find movie"
              auto-select
              @update="handleUpdate"
              @submit="handleAutocompleteSubmit"
            ></autocomplete>
            <button type="submit" class="poss-search">
              <img
                src="~/assets/images/search.svg"
                width="20"
                class="mr-2 mt-1"
                aria-expanded="true"
                aria-haspopup="true"
              />
            </button>
          </div>
        </form>
      </div>
      <div class="w-1/3 flex items-center flex-shrink-0 h-10">
        <div class="text-sm lg:flex-none flex-none ml-10">
          <button
            type="button"
            class="lg:mt-0 text-white mr-7 category"
            aria-expanded="true"
            aria-haspopup="true"
            @click="openDropDown"
          >
            <img
              src="~/assets/images/category.svg"
              width="20"
              class="mr-2"
              aria-expanded="true"
              aria-haspopup="true"
            />
            <span>CATEGORIES</span>
          </button>
          <nuxt-link
            to="/movie"
            class="block lg:inline-block lg:mt-0 text-white mr-7"
          >
            MOVIES
          </nuxt-link>
          <nuxt-link
            to="/movie"
            class="block lg:inline-block lg:mt-0 text-white mr-7"
          >
            TV SHOWS
          </nuxt-link>
          <nuxt-link
            to="/movie"
            class="block lg:inline-block lg:mt-0 text-white mr-7"
          >
            LOGIN
          </nuxt-link>
        </div>
        <div
          class="absolute z-10 mt-12 ml-6 w-40 rounded-md bg-white shadow-lg top-0"
          role="menu"
          aria-orientation="vertical"
          aria-labelledby="menu-button"
          tabindex="-1"
          v-if="dropDown"
        >
          <div
            class="py-1"
            role="none"
            v-for="movie in listGenre"
            :key="movie"
            @click="openDropDown"
          >
            <nuxt-link
              :to="`/movie?genre=${movie}`"
              class="text-gray-700 block px-4 py-2 text-sm font-bold uppercase"
              role="menuitem"
              @click="setCategory(`${movie}`)"
            >
              {{ movie }}
            </nuxt-link>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Autocomplete from "@trevoreyre/autocomplete-vue";

export default {
  name: "Header",

  components: {
    Autocomplete,
  },

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
      listSearch: this.movieData.map((x) => x.Title),
    };
  },

  methods: {
    openDropDown() {
      this.dropDown = !this.dropDown;
    },
    setCategory(e) {
      this.dropDown = !this.dropDown;
    },

    search(input) {
      this.submitted = false;
      if (input.length < 1) {
        return [];
      }
      return this.listSearch.filter((data) => {
        return data.toLowerCase().startsWith(input.toLowerCase());
      });
    },

    handleUpdate(results, selectedIndex) {
      this.results = results;
      this.selectedIndex = selectedIndex;
    },

    handleFormSubmit(event) {
      event.preventDefault();
      if (!this.submitted) {
        const result = this.results[this.selectedIndex];
        this.handleSubmit(result);
      }
    },

    handleAutocompleteSubmit(result) {
      if (result !== undefined) {
        this.submitted = true;
        let imdbIDSearch = this.movieData.find((x) => x.Title === result);
        this.$router.push(`/detail?imdbID=${imdbIDSearch.imdbID}`);
      }
      // this.handleSubmit(result);
    },

    // handleSubmit(result) {
    //   this.submittedResult = result;
    // },
  },
};
</script>

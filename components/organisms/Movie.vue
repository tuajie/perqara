<template>
  <div class="mt-8 pt-8">
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
              {{ filter }}
            </button>
          </div>
          <div
            class="inline-flex w-68 justify-left bg-black-true px-1 py-1 text-sm font-small text-white shadow-sm mr-4 ml-4 py-2"
            role="menu"
            aria-orientation="vertical"
            aria-labelledby="menu-button"
            tabindex="-1"
            v-show="dropDown"
          >
            <div class="py-1" role="none">
              <a
                href="#"
                class="text-white-700 block px-4 py-2 text-sm"
                role="menuitem"
                @click="setFilter('Popularity Ascending')"
                >Popularity Ascending</a
              >
              <a
                href="#"
                class="text-white-700 block px-4 py-2 text-sm"
                role="menuitem"
                @click="setFilter('Popularity Descending')"
                >Popularity Descending</a
              >
              <a
                href="#"
                class="text-white-700 block px-4 py-2 text-sm"
                role="menuitem"
                @click="setFilter('Release Date Descending')"
                >Release Date Ascending</a
              >
              <a
                href="#"
                class="text-white-700 block px-4 py-2 text-sm"
                role="menuitem"
                @click="setFilter('Release Date Descending')"
                >Release Date Descending</a
              >
              <a
                href="#"
                class="text-white-700 block px-4 py-2 text-sm"
                role="menuitem"
                @click="setFilter('Rating Ascending')"
                >Rating Ascending</a
              >
              <a
                href="#"
                class="text-white-700 block px-4 py-2 text-sm"
                role="menuitem"
                @click="setFilter('Rating Descending')"
                >Rating Descending</a
              >
            </div>
          </div>
        </div>
        <h4 class="mb-4 mt-4 pt-3 pb-3 px-4 border-btm-top">Genres</h4>
        <div class="flex justify-between item">
          <label for="checked-Action" class="label-chck pl-4 pl-4"
            >Action</label
          >
          <input
            id="checked-Action"
            type="checkbox"
            value=""
            class="w-4 h-4 text-red-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 mr-4"
          />
        </div>
        <div class="flex justify-between item">
          <label for="checked-Adventure" class="label-chck pl-4"
            >Adventure</label
          >
          <input
            id="checked-Adventure"
            type="checkbox"
            value=""
            class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 mr-4"
          />
        </div>
        <div class="flex justify-between item">
          <label for="checked-Animation" class="label-chck pl-4"
            >Animation</label
          >
          <input
            id="checked-Animation"
            type="checkbox"
            value=""
            class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 mr-4"
          />
        </div>
        <div class="flex justify-between item">
          <label for="checked-Comedy" class="label-chck pl-4">Comedy</label>
          <input
            id="checked-Comedy"
            type="checkbox"
            value=""
            class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 mr-4"
          />
        </div>
        <div class="flex justify-between item">
          <label for="checked-Crime" class="label-chck pl-4">Crime</label>
          <input
            id="checked-Crime"
            type="checkbox"
            value=""
            class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 mr-4"
          />
        </div>
        <div class="flex justify-between item">
          <label for="checked-Documentary" class="label-chck pl-4"
            >Documentary</label
          >
          <input
            id="checked-Documentary"
            type="checkbox"
            value=""
            class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 mr-4"
          />
        </div>
        <div class="flex justify-between item">
          <label for="checked-Drama" class="label-chck pl-4">Drama</label>
          <input
            id="checked-Drama"
            type="checkbox"
            value=""
            class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 mr-4"
          />
        </div>
        <div class="flex justify-between item">
          <label for="checked-Family" class="label-chck pl-4">Family</label>
          <input
            id="checked-Family"
            type="checkbox"
            value=""
            class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 mr-4"
          />
        </div>
        <div class="flex justify-between item">
          <label for="checked-Fantasy" class="label-chck pl-4">Fantasy</label>
          <input
            id="checked-Fantasy"
            type="checkbox"
            value=""
            class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 mr-4"
          />
        </div>
        <div class="flex justify-between item">
          <label for="checked-History" class="label-chck pl-4">History</label>
          <input
            id="checked-History"
            type="checkbox"
            value=""
            class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 mr-4"
          />
        </div>
        <div class="flex justify-between item">
          <label for="checked-Horror" class="label-chck pl-4">Horror</label>
          <input
            id="checked-Horror"
            type="checkbox"
            value=""
            class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 mr-4"
          />
        </div>
      </div>
      <div class="w-4/5">
        <div class="container mx-auto grid grid-cols-4 gap-8">
          <Card />
          <Card />
          <Card />
          <Card />
          <Card />
          <Card />
          <Card />
          <Card />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Card from "../molecules/Card.vue";
export default {
  name: "Movie",
  components: { Card },

  data() {
    return {
      dropDown: false,
      filter: "Popularity Ascending",
    };
  },

  methods: {
    openDropDown() {
      this.dropDown = !this.dropDown;
    },
    setFilter(value) {
      this.filter = value;
      this.dropDown = !this.dropDown;
    },
  },
};
</script>

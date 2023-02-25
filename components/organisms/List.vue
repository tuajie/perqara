<template>
  <div class="mt-8 pt-8">
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
          <div class="py-1" role="none">
            <a
              href="#"
              class="text-gray-700 block px-4 py-2 text-sm"
              role="menuitem"
              @click="setFilter('Popularity Ascending')"
              >Popularity Ascending</a
            >
            <a
              href="#"
              class="text-gray-700 block px-4 py-2 text-sm"
              role="menuitem"
              @click="setFilter('Popularity Descending')"
              >Popularity Descending</a
            >
            <a
              href="#"
              class="text-gray-700 block px-4 py-2 text-sm"
              role="menuitem"
              @click="setFilter('Release Date Descending')"
              >Release Date Ascending</a
            >
            <a
              href="#"
              class="text-gray-700 block px-4 py-2 text-sm"
              role="menuitem"
              @click="setFilter('Release Date Descending')"
              >Release Date Descending</a
            >
            <a
              href="#"
              class="text-gray-700 block px-4 py-2 text-sm"
              role="menuitem"
              @click="setFilter('Rating Ascending')"
              >Rating Ascending</a
            >
            <a
              href="#"
              class="text-gray-700 block px-4 py-2 text-sm"
              role="menuitem"
              @click="setFilter('Rating Descending')"
              >Rating Descending</a
            >
          </div>
        </div>
      </div>
    </div>
    <div class="container mx-auto grid grid-cols-5 gap-8 pt-8">
      <Card />
      <Card />
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
</template>

<script>
import Card from "../molecules/Card.vue";
export default {
  name: "List",
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

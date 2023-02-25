<template>
  <div class="mt-8 pt-8">
    <div class="container mx-auto list-title grid grid-cols-5"></div>
    <div class="container mx-auto grid grid-cols-5 gap-8 pt-8">
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
  name: "Detail",
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

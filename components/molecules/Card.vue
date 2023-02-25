<template>
  <div
    class="bg-black card-movie"
    @mouseover="mouseOver"
    @mouseleave="mouseLeave"
  >
    <a href="#">
      <div class="flex flex-row-reverse">
        <span class="rate pr-2 pl-2">7.0</span>
      </div>
      <div v-show="upHere" class="hover-abs">
        <div class="hover grid grid-cols-1 content-center">
          <h3 class="mb-4">
            <img
              src="~/assets/images/Star.svg"
              width="24"
              class="mt-2 mr-1"
            /><span>7.3</span>
          </h3>
          <h4 class="mb-4 mt-2">Action</h4>
          <button class="text-white py-0 px-2 rounded-full mt-4">view</button>
        </div>
      </div>
      <img
        class=""
        src="https://m.media-amazon.com/images/M/MV5BZWI3ZThmYzUtNDJhOC00ZWY4LThiNmMtZDgxNjE3Yzk4NDU1XkEyXkFqcGdeQXVyNTk5Nzg1NjQ@._V1_SX300.jpg"
        alt=""
      />
    </a>

    <div class="pt-2 pb-2">
      <a href="#">
        <h5
          class="mb-1 text-1xl font-bold tracking-tight text-gray-900 dark:text-white"
        >
          Noteworthy technology acquisitions 2021
        </h5>
      </a>
      <p class="mb-1 font-normal text-gray-700 dark:text-gray-400">2020</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",

  data() {
    return {
      upHere: false,
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

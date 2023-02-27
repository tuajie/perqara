<template>
  <div class="bg-white">
    <div
      :style="{
        backgroundImage: `url(${require(`@/assets/images/poster-bg.jpeg`)})`,
      }"
      class="bg-movie"
    >
      <div class="layer"></div>
      <div class="bottom-bg"></div>
    </div>
    <div class="relative container mx-auto detail-position mb-0">
      <div class="grid grid-cols-5 grid-flow-col gap-4">
        <div class="row-span-5">
          <img
            class=""
            :src="`${dataDetail.Poster}`"
            :alt="`${dataDetail.Title}`"
          />
        </div>
        <div class="col-span-7 grid-flow-col text-white info-movie pl-4">
          <div class="year pt-4">{{ dataDetail.Year }}</div>
          <div class="title">{{ dataDetail.Title }}</div>
          <div class="genre">{{ dataDetail.Genre }}</div>
          <div class="grid grid-flow-col pt-10">
            <div class="absolute bg-info"></div>
            <div class="star">
              <img
                src="~/assets/images/Star.svg"
                width="34"
                class="mt-2 mr-2"
              />
              <h5 class="rate">{{ dataDetail.imdbRating }}</h5>
            </div>
            <div class="more-info pl-1">
              <label>User Score</label>
              <p>{{ dataDetail.imdbVotes }} Votes</p>
            </div>
            <div class="more-info pl-6">
              <label>Status</label>
              <p>{{ dataDetail.Year }}</p>
            </div>
            <div class="more-info pl-6">
              <label>Language</label>
              <p>{{ dataDetail.Language }}</p>
            </div>
            <div class="more-info pl-6">
              <label>Budget</label>
              <p>$200,000,000.00</p>
            </div>
            <div class="more-info more-info-last pl-6">
              <label>Production</label>
              <p>{{ dataDetail.Production }}</p>
            </div>
          </div>
          <div class="mt-8 text-black overview">
            <h4 class="mb-2">OVERVIEW</h4>
            <p class="">
              {{ dataDetail.Plot }}
            </p>
          </div>
        </div>
      </div>
      <div class="review mb-4 mt-6">
        <h4 class="mb-2">REVIEW</h4>
        <div class="container mx-auto grid grid-cols-2 gap-8">
          <div class="w-full rounded-lg overflow-hidden shadow-lg card p-6">
            <div class="flex justify-between">
              <div class="grid grid-rows-3 grid-flow-col">
                <div class="row-span-3 avatar"></div>
                <h5 class="col-span-2 pl-4 pt-1">SWITCH.</h5>
                <p class="col-span-2 pl-4">December 18, 2020</p>
              </div>
              <div class="star-rate rounded-lg p-0 pl-2">
                <img
                  src="~/assets/images/Star.svg"
                  width="20"
                  class="mt-3 mr-2"
                />
                <h6>7.0</h6>
              </div>
            </div>
            <div class="content">
              <p class="text-gray-700">
                It isn't as easy as saying 'Wonder Woman 1984' is a good or bad
                movie. The pieces are there, and there are moments I adore, but
                it does come across as a bit of a mess, even though the action
                sequences are breathtaking. If you're a fan of the original
                film, you'll be more willing to take the ride, but for those
                more indifferent, it may be a bit of a blander sit. If you can
                and are planning to watch it, the theatrical experience is the
                way to go - there is nothing like seeing these stunning sets,
                fun action scenes and hearing Zimmer's jaw-dropping score like
                on the big screen. - Chris dos Santos...
                <span>read the rest</span>
              </p>
            </div>
          </div>
          <div class="w-full rounded-lg overflow-hidden shadow-lg card p-6">
            <div class="flex justify-between">
              <div class="grid grid-rows-3 grid-flow-col">
                <div class="row-span-3 avatar"></div>
                <h5 class="col-span-2 pl-4 pt-1">msbreviews</h5>
                <p class="col-span-2 pl-4">December 18, 2020</p>
              </div>
              <div class="star-rate rounded-lg p-0 pl-2">
                <img
                  src="~/assets/images/Star.svg"
                  width="20"
                  class="mt-3 mr-2"
                />
                <h6>8.0</h6>
              </div>
            </div>
            <div class="content">
              <p class="text-gray-700">
                If you enjoy reading my Spoiler-Free reviews, please follow my
                blog @ https://www.msbreviews.com The superhero genre has been
                growing exponentially during the last decade, so it's bizarre to
                go through an entire year with only Birds of Prey and The New
                Mutants instead of literally dozens of films from both Marvel
                and DC. Thankfully, Warner Bros. decided to release Wonder Woman
                1984 before the year's end, but not without a catch. Most people
                will only have the possibility of watching one of the few
                blockbusters of 2020 through HBO Max, a streaming service only
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="w-full bg-black pt-6 mt-min-10">
      <div class="container mx-auto pt-6 recomend">
        <h4 class="pb-8">RECOMMENDATION MOVIES</h4>
        <div class="container mx-auto grid grid-cols-5 gap-8">
          <div v-for="movie in movieData.slice(0, 5)" :key="movie.id">
            <Card :movie="movie" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Card from "../molecules/Card.vue";
import MovieData from "../../assets/json/movie.json";

export default {
  name: "MovieDetail",
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
      MovieData: MovieData,
      imdbID: this.$route.query.imdbID,
      dataDetail: {},
    };
  },

  mounted() {
    this.findDataDetail();
  },

  watch: {
    async $route(to, from) {
      let queryNow = this.$route.query.imdbID;
      let data = this.MovieData.find((x) => x.imdbID === queryNow);
      this.dataDetail = data;
    },
  },

  methods: {
    openDropDown() {
      this.dropDown = !this.dropDown;
    },
    setFilter(value) {
      this.filter = value;
      this.dropDown = false;
    },
    findDataDetail() {
      let data = this.MovieData.find((x) => x.imdbID === this.imdbID);
      this.dataDetail = data;
    },
  },
};
</script>

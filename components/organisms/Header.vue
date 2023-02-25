<template>
  <div class="bg-black p-2">
    <div class="flex mb-4 container mx-auto pt-2">
      <div class="w-1/6 flex items-center flex-shrink-0 h-10">
        <img src="~/assets/images/MoovieTime-Logo.svg" width="100" />
      </div>
      <div class="w-1/2 h-10">
        <form class="block flex-none">
          <div class="mb-4">
            <input
              class="appearance-none border-gray rounded w-full py-2 px-3 bg-input text-white leading-tight focus:outline-none focus:shadow-outline"
              id="username"
              type="text"
              placeholder="Find movie"
            />
          </div>
        </form>
      </div>
      <div class="w-1/3 flex items-center flex-shrink-0 h-10">
        <div class="text-sm lg:flex-none flex-none ml-10">
          <a
            href="#responsive-header"
            class="block lg:inline-block lg:mt-0 text-white mr-7"
          >
            <!-- <svg
              class="fill-current h-3 w-3"
              viewBox="0 0 20 20"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z" /></svg
            > -->
            CATEGORIES
          </a>
          <a
            href="#responsive-header"
            class="block lg:inline-block lg:mt-0 text-white mr-7"
          >
            MOVIES
          </a>
          <a
            href="#responsive-header"
            class="block lg:inline-block lg:mt-0 text-white mr-7"
          >
            TV SHOWS
          </a>
          <a
            href="#responsive-header"
            class="block lg:inline-block lg:mt-0 text-white"
          >
            LOGIN
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

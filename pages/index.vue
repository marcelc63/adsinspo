<template>
  <div class="flex flex-row">
    <div class="w-full py-4 lg:py-8 px-4 lg:px-10 flex flex-col">
      <div class="flex flex-col mb-4">
        <p class="text-purple-400 font-bold mb-2">Apps Inspiration</p>
        <p class="text-5xl font-extrabold mb-2">
          456+ Tech Apps Ads Inspiration
        </p>
        <p class="text-sm mb-1 text-purple-400">Filter Category</p>

        <div class="flex flex-row">
          <router-link to="/">
            <p
              class="mr-1 px-2 rounded border-2 border-purple-300 text-purple-400 text-sm hover:bg-purple-200 hover:text-purple-800 cursor-pointer"
            >
              All
            </p>
          </router-link>
          <router-link to="/inspiration/apps">
            <p
              class="mr-1 px-2 rounded border-2 border-purple-300 text-sm bg-purple-200 text-purple-800 cursor-pointer"
            >
              Apps
            </p>
          </router-link>
          <router-link to="/inspiration/fnb">
            <p
              class="mr-1 px-2 rounded border-2 border-purple-300 text-purple-400 text-sm hover:bg-purple-200 hover:text-purple-800 cursor-pointer"
            >
              FnB
            </p>
          </router-link>
          <router-link to="/inspiration/services">
            <p
              class="mr-1 px-2 rounded border-2 border-purple-300 text-purple-400 text-sm hover:bg-purple-200 hover:text-purple-800 cursor-pointer"
            >
              Services
            </p>
          </router-link>
          <router-link to="/inspiration/goods">
            <p
              class="mr-1 px-2 rounded border-2 border-purple-300 text-purple-400 text-sm hover:bg-purple-200 hover:text-purple-800 cursor-pointer"
            >
              Goods
            </p>
          </router-link>
        </div>
      </div>
      <div class="flex flex-row flex-wrap mb-4">
        <div class="w-12/12 md:w-3/12 p-2" v-for="index in 8" :key="index">
          <img
            src="/ads/ad2.jpg"
            class="radius-2 shadow-md"
            crossorigin="use-credentials"
          />
        </div>
      </div>
      <div class="flex flex-row justify-center">
        <div
          class="rounded bg-purple-600 text-white px-2 py-1 font-bold text-2xl"
        >
          Load More
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  created: function () {
    console.log('hey!')
  },
})
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
</style>

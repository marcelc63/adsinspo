<template>
  <div class="flex flex-row justify-center">
    <div
      class="w-full py-4 lg:py-8 px-4 lg:px-10 flex flex-col max-w-screen-xl"
    >
      <div class="flex flex-col mb-4">
        <p class="text-purple-400 font-bold mb-2">Inspiration</p>
        <p class="text-5xl font-extrabold mb-2">
          {{ images.length }}+ {{ title }}
        </p>

        <div class="flex flex-row flex-wrap">
          <Link to="/" :active="!$route.params.tag">All</Link>
          <Link to="/inspiration/tech" :active="$route.params.tag === 'tech'"
            >Tech</Link
          >
          <Link to="/inspiration/fnb" :active="$route.params.tag === 'fnb'"
            >F&B</Link
          >
          <Link
            to="/inspiration/services"
            :active="$route.params.tag === 'services'"
            >Services</Link
          >
          <Link to="/inspiration/goods" :active="$route.params.tag === 'goods'"
            >Goods</Link
          >
          <Link
            to="/inspiration/education"
            :active="$route.params.tag === 'education'"
            >Education</Link
          >
          <Link to="/inspiration/game" :active="$route.params.tag === 'game'"
            >Game</Link
          >
        </div>
      </div>
      <div class="flex flex-row flex-wrap mb-4">
        <div
          class="w-12/12 md:w-3/12 p-2"
          v-for="(image, index) in images.slice(0, max)"
          :key="index"
        >
          <img
            :data-src="image.public_id | cloudinaryImageUrl"
            class="radius-2 shadow-md"
            crossorigin="anonymous"
            v-lazy-load
          />
        </div>
      </div>
      <div class="flex flex-row justify-center">
        <div
          @click="loadMore"
          class="rounded bg-purple-600 text-white px-2 py-1 font-bold text-2xl cursor-pointer"
        >
          Load More
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import cl from '~/plugins/cloudinary'

export default Vue.extend({
  created: async function () {
    let url = await cl.url(`${this.$route.params.tag || 'ads'}.json`, {
      type: 'list',
    })
    await this.fetchImageList(url)
  },
  data() {
    return {
      images: new Array(),
      max: 8,
    }
  },
  computed: {
    title(): string {
      return this.$route.params.tag
        ? `${this.$route.params.tag.toUpperCase()} ADS INSPIRATION`
        : `IG ADS INSPIRATION`
    },
  },
  filters: {
    cloudinaryImageUrl(public_id: string): string {
      let src = cl.url(public_id)
      return src
    },
  },
  methods: {
    async fetchImageList(url: string) {
      const list = await this.$axios.$get(url)
      this.images = list.resources.sort(() => 0.5 - Math.random())
    },
    loadMore(): void {
      this.max += 8
    },
  },
})
</script>
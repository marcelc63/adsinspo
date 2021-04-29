<template>
  <router-link :to="to">
    <p
      class="mr-1 mb-1 px-2 py-1 rounded border-2 border-purple-300 text-sm bg-purple-200 text-purple-800 cursor-pointer"
      v-if="active"
    >
      <slot></slot>
    </p>
    <p
      class="mr-1 mb-1 px-2 py-1 rounded border-2 border-purple-300 text-purple-400 text-sm hover:bg-purple-200 hover:text-purple-800 cursor-pointer"
      v-if="!active"
    >
      <slot></slot>
    </p>
  </router-link>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  props: {
    active: Boolean,
    to: String,
  },
})
</script>
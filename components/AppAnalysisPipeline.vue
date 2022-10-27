<script setup lang="ts">
import { computed, ref } from 'vue'

const props = defineProps({
  // clicks: {
  //   default: 0,
  // },
  cover: {
    default: true,
  },
  animation: {
    default: 0,
  },
})

// console.log(props.clicks)

// $slidev.nav.clicks = props.clicks

const additionalClass = computed(() => {
  if ($slidev.nav.clicks < props.animation) {
    return 'mt-50'
  }
  return 'mt-0'
})
</script>

<template>
  <div :class="['transition-all duration-700 flex flex-row justify-center text-xl', additionalClass]">
    <span>Film</span>
    <span class="mx-3"><mdi-arrow-right-thick /></span>
    <span>Parameter definieren</span>
    <span class="mx-3"><mdi-arrow-right-thick /></span>
    <span>Analyse</span>
    <span class="mx-3"><mdi-arrow-right-thick /></span>
    <span>Auswertung</span>
    <span class="mx-3"><mdi-arrow-right-thick /></span>
    <span>Erkenntnisse</span>
  </div>

  <div class="absolute w-50 mt-15" v-if="props.cover">
    <img src="/assets/movie-covers/tmdb-120.jpg" />
    <div class="text-right text-xs">
      &copy; themoviedb.org
    </div>
  </div>
</template>

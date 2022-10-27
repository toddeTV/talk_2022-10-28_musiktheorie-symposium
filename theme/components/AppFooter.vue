<script setup lang="ts">
defineProps({
  website: {
    type: String,
  },
})
</script>

<template>
  <footer class="flex flex-col justify-between w-full mt-auto text-blue-500 dark:text-white">
    <div class="flex justify-between w-full text-blue-500 dark:text-white">
      <a v-if="website || $slidev.configs.author.website"
         :href="'https://' + (website || $slidev.configs.author.website)"
         target="_blank"
         class="mb-0 baseColor !border-b-0">
          @{{ website || $slidev.configs.author.website }}</a>
      <span>{{ $slidev.nav.currentPage }}</span>
    </div>
  </footer>
</template>

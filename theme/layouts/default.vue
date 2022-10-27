<script setup lang="ts">
import AppFooter from '../components/AppFooter.vue'
defineProps({
  website: {
    type: String,
  },
})
</script>

<template>
  <div class="bg-main slidev-layout flex flex-col h-full">
    <div class="mt-auto mb-auto flex-grow">
      <slot />
    </div>
    <AppFooter
      :website="website"
    />
  </div>
</template>

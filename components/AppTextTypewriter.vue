<script setup lang="ts">
import { ref } from 'vue'
import { useTypewriter } from '@altgen/typer-composable'
import { useInterval } from '@vueuse/core'

const props = defineProps({
  text: String,
})

const strings = ref(
  props.text!.split('|'),
)

const {
  text,
  currentString,
  currentAction
} = useTypewriter(strings, {
  startEmpty: true,
  holdFor: 4000,
  holdEmptyFor: 1000,
  shuffle: false,
  loop: true,
})

const cursorCounter = ref(0)
const counter = useInterval(200, {
  callback: () => {
    if (currentAction.value !== 2){
      cursorCounter.value = 1
      return
    }
    cursorCounter.value += 1
    if (cursorCounter.value > 5){
      cursorCounter.value = -1
    }
  }
})
</script>

<template>
  <div class="h-10 w-full text-left flex flex-row justify-start">
    <span aria-hidden="true">{{ text }}</span>
    <span class="ml-0.5 -mt-0.5 h-6 w-0.5 bg-gray-500 dark:bg-gray-100" v-if="cursorCounter > 0" />
  </div>
</template>

<template>
  <ClientOnly>
    <UButton
        :icon="isDark ? 'i-heroicons-moon-20-solid' : 'i-heroicons-sun-20-solid'"
        color="gray"
        variant="ghost"
        aria-label="Theme"
        @click="isDark = !isDark"
    />

    <template #fallback>
      <div class="w-8 h-8"/>
    </template>
  </ClientOnly>
</template>

<script setup>
import {computed} from "vue";
import {useColorMode} from "@nuxtjs/color-mode/dist/runtime/composables.js";
const colorMode = useColorMode()

const isDark = computed({
  get() {
    return colorMode.value === 'dark'
  },
  set() {
    colorMode.preference = colorMode.value === 'dark' ? 'light' : 'dark'
  }
})
</script>

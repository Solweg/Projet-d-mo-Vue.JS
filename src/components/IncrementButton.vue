<script setup>
import { ref } from 'vue'

const count = ref(0)

function increment() {
  count.value++
}
</script>

<template>
  <div class="p-4 flex flex-col items-center gap-4">
    <p class="text-xl font-semibold">
      Valeur actuelle : <span class="text-blue-600">{{ count }}</span>
    </p>

    <button 
      @click="increment"
      class="px-4 py-2 bg-blue-500 text-white rounded-lg hover:bg-blue-600 transition-colors shadow-md"
    >
      Incrémenter
    </button>
  </div>
</template>

<style scoped>

</style>
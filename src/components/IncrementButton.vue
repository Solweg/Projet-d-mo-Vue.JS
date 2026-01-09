<script setup>
import { ref } from 'vue'

defineProps({
  titreBouton: { type: String, default: 'Compteur' }
})

const emettre = defineEmits(['valeurMiseAJour'])
const compteur = ref(0)

function incrementer() {
  compteur.value++
  emettre('valeurMiseAJour', compteur.value)
}
</script>

<template>
  <div class="flex flex-col items-center p-4 border rounded-lg bg-white shadow">
    <span class="text-gray-500 font-bold mb-2">{{ titreBouton }}</span>
    <button 
      @click="incrementer"
      class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600 transition"
    >
      <slot :compteur="compteur">
        Valeur par défaut : {{ compteur }}
      </slot>
    </button>
  </div>
</template>
<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const props = defineProps({
  titreBouton: { type: String, default: 'Compteur' }
})
const emettre = defineEmits(['valeurMiseAJour'])
const compteur = ref(0)

function incrementer() {
  compteur.value++
  emettre('valeurMiseAJour', compteur.value)
}

// Hook pour confirmer que chaque bouton de la liste est bien monté
onMounted(() => console.log(`${props.titreBouton} est prêt !`))
</script>

<template>
  <div class="flex flex-col items-center p-4 border rounded-lg bg-white shadow-sm">
    <span class="text-gray-400 text-xs font-black mb-3 uppercase">{{ titreBouton }}</span>
    <button @click="incrementer" class="rounded-lg transition active:scale-95">
      <slot :compteur="compteur">
        <div class="px-4 py-2 bg-blue-500 text-white rounded-lg">Valeur : {{ compteur }}</div>
      </slot>
    </button>
  </div>
</template>
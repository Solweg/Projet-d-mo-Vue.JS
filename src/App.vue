<script setup>
import { ref } from 'vue'
import IncrementButton from "./components/IncrementButton.vue";

// variables pour le v-model et le v-if
const nomUtilisateur = ref("")
const afficherListe = ref(true)

// liste pour le v-for
const couleurs = ref([
  { nom: 'Indigo', classe: 'bg-indigo-500 hover:bg-indigo-600' },
  { nom: 'Émeraude', classe: 'bg-emerald-500 hover:bg-emerald-600' },
  { nom: 'Rose', classe: 'bg-rose-500 hover:bg-rose-600' }
])

const logChangement = (nom, val) => console.log(`${nom} : ${val}`);
</script>

<template>
  <div class="min-h-screen bg-indigo-100 p-8 flex flex-col items-center gap-8">
    
    <h1 class="text-3xl font-black text-indigo-900">Mon TP Vue Complet</h1>

    <div class="bg-white p-4 rounded-xl shadow">
      <input v-model="nomUtilisateur" placeholder="Ton nom" class="border p-2 rounded" />
      <p v-if="nomUtilisateur">Bienvenue, {{ nomUtilisateur }} !</p>
    </div>

    <button @click="afficherListe = !afficherListe" class="bg-white px-4 py-2 rounded-full shadow font-bold">
      {{ afficherListe ? '🗑️ Cacher la liste (Démontage)' : '✨ Afficher la liste (Montage)' }}
    </button>

    <div v-if="afficherListe" class="grid grid-cols-1 md:grid-cols-3 gap-6 w-full max-w-4xl">
      <div v-for="(item, index) in couleurs" :key="index">
        <IncrementButton 
          :titreBouton="item.nom" 
          @valeurMiseAJour="(val) => logChangement(item.nom, val)"
        >
          <template #default="{ compteur }">
            <div :class="[item.classe, 'text-white px-6 py-3 rounded-xl font-bold shadow-md']">
               {{ item.nom }} : {{ compteur }}
            </div>
          </template>
        </IncrementButton>
      </div>
    </div>

    <p v-else class="text-indigo-400 italic">La liste a été supprimée du DOM.</p>

  </div>
</template>
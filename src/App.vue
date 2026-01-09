<script setup>
import IncrementButton from "./components/IncrementButton.vue";
</script>

<template>
  <div class="min-h-screen bg-gray-50 flex flex-col items-center justify-center gap-8">
    
    <div class="text-center">
      <p class="text-sm text-gray-400 mb-2">Bouton Standard :</p>
      <IncrementButton titreBouton="Compteur Simple" />
    </div>

    <div class="text-center">
      <p class="text-sm text-gray-400 mb-2">Bouton avec Slot :</p>
      <IncrementButton titreBouton="Compteur Personnalisé">
        <template #default="slotProps">
          <span>Je suis un bouton incrémental : <strong>{{ slotProps.compteur }}</strong></span>
        </template>
      </IncrementButton>
    </div>

  </div>
</template>
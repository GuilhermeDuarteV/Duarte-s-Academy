<template>
  <div class="notes">
    <h3>Bloco de Notas - Cargas</h3>
    <textarea v-model="note" placeholder="Anote os pesos e observações..."></textarea>
    <button @click="saveNote">Salvar</button>
    <p v-if="saved">Anotação salva!</p>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const note = ref('')
const saved = ref(false)

const saveNote = () => {
  localStorage.setItem('training_note', note.value)
  saved.value = true
  setTimeout(() => saved.value = false, 2000)
}

onMounted(() => {
  note.value = localStorage.getItem('training_note') || ''
})
</script>

<style scoped>
.notes {
  margin-top: 2rem;
}
textarea {
  width: 100%;
  height: 100px;
  margin-bottom: 1rem;
}
button {
  padding: 0.5rem 1rem;
}
</style>

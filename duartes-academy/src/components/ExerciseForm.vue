<template>
  <div class="exercise-form">
    <h3>Montar Treino</h3>
    <form @submit.prevent="addExercise">
      <select v-model="selectedDay" required>
        <option disabled value="">Escolha o dia</option>
        <option v-for="(d, i) in days" :key="i" :value="d">{{ d }}</option>
      </select>
      <input v-model="exercise" placeholder="Nome do exercício" required />
      <button type="submit">Adicionar</button>
    </form>
    <div v-if="exercises.length">
      <h4>Exercícios Cadastrados:</h4>
      <ul>
        <li v-for="(e, i) in exercises" :key="i">
          {{ e.day }} - {{ e.name }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const selectedDay = ref('')
const exercise = ref('')
const exercises = ref([])

const days = ['Segunda-feira', 'Terça-feira', 'Quarta-feira', 'Quinta-feira', 'Sexta-feira']

const addExercise = () => {
  exercises.value.push({ day: selectedDay.value, name: exercise.value })
  exercise.value = ''
  selectedDay.value = ''
}
</script>

<style scoped>
.exercise-form {
  margin-top: 2rem;
}
input, select {
  margin: 0.5rem;
  padding: 0.5rem;
}
button {
  padding: 0.5rem 1rem;
}
</style>

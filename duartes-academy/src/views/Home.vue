<template>
  <div class="dashboard">
    <aside class="sidebar">
      <h2>Dias da Semana</h2>
      <ul>
        <li v-for="day in days" :key="day" @click="selectDay(day)" :class="{ active: selectedDay === day }">
          {{ day }}
        </li>
      </ul>
      <button @click="logout">Sair</button>
    </aside>

    <main class="main">
      <div class="card">
        <h2>{{ selectedDay }}</h2>
        <ExerciseForm :day="selectedDay" />
      </div>

      <div class="card">
        <Notes :day="selectedDay" />
      </div>
    </main>
  </div>
</template>

<script setup>
import ExerciseForm from '@/components/ExerciseForm.vue'
import Notes from '@/components/Notes.vue'
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const days = ['Segunda', 'Terça', 'Quarta', 'Quinta', 'Sexta']
const selectedDay = ref(days[0])

function logout() {
  localStorage.removeItem('user')
  router.push('/')
}

function selectDay(day) {
  selectedDay.value = day
}
</script>

<style scoped>
.dashboard {
  display: flex;
  min-height: 100vh;
}

.sidebar {
  background-color: #1e293b;
  color: white;
  padding: 2rem;
  width: 240px;
}

.sidebar h2 {
  margin-bottom: 1rem;
}

.sidebar ul {
  list-style: none;
  padding: 0;
}

.sidebar li {
  padding: 0.5rem 0;
  cursor: pointer;
  border-bottom: 1px solid #334155;
}

.sidebar li.active {
  font-weight: bold;
  color: var(--accent-color);
}

.sidebar button {
  margin-top: 2rem;
  background: #ef4444;
}

.main {
  flex-grow: 1;
  padding: 2rem;
}
</style>

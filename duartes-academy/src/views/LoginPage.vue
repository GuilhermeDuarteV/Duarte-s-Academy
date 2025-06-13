<template>
  <div class="login-container">
    <div class="login-box">
      <h1>Duarte's Academy</h1>
      <p class="subtitle">Seu app de treinos e progresso</p>
      <form @submit.prevent="login">
        <label for="email">Email</label>
        <input type="email" v-model="email" required />

        <label for="password">Senha</label>
        <input type="password" v-model="password" required />

        <button type="submit">Entrar</button>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const email = ref('')
const password = ref('')
const router = useRouter()

function login() {
  // Simulação de login
  localStorage.setItem('user', JSON.stringify({ email: email.value }))
  router.push('/home')
}
</script>

<style scoped>
.login-container {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background: linear-gradient(to right, #3b82f6, #22c55e);
}

.login-box {
  background-color: white;
  padding: 2.5rem;
  border-radius: 16px;
  box-shadow: var(--shadow);
  width: 100%;
  max-width: 400px;
  text-align: center;
}

h1 {
  font-size: 2rem;
  color: #333;
}

.subtitle {
  color: #666;
  margin-bottom: 2rem;
  font-size: 1rem;
}

form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
</style>

<script setup>
import { ref, onMounted, watch } from 'vue'

const week = ref([
  { day: 'Segunda-feira', exercises: [] },
  { day: 'Terça-feira', exercises: [] },
  { day: 'Quarta-feira', exercises: [] },
  { day: 'Quinta-feira', exercises: [] },
  { day: 'Sexta-feira', exercises: [] },
])

onMounted(() => {
  const saved = localStorage.getItem('weekdays')
  if (saved) {
    week.value = JSON.parse(saved)
  }
})

watch(week, (newVal) => {
  localStorage.setItem('weekdays', JSON.stringify(newVal))
}, { deep: true })
</script>

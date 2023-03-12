<script setup lang="ts">
  import { defineProps } from 'vue'
  import { RouterLink } from 'vue-router'

  const { 
    questionsLength, 
    numberOfCorrectAnswers
  } = defineProps([
    'questionsLength', 
    'numberOfCorrectAnswers'
  ])
</script>

<template>
  <div class="results">
    <p>Yure results...</p>
    <h1>{{ numberOfCorrectAnswers }}/{{ questionsLength }}</h1>
  </div>
  <RouterLink to="/">Go home</RouterLink>
</template>

<style scoped>
.results {
  text-align: center;
  padding: 100px 0;
}

p {
  font-size: 25px;
}

h1 {
  font-size: 80px;
}
</style>
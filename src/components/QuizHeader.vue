<script setup lang="ts">
  import { defineProps } from 'vue'

  const { 
    questionStatus, 
    barPercentage 
  } = defineProps([
    'questionStatus', 
    'barPercentage'
  ]) 
</script>

<template>
  <header>
    <h4>Question {{ questionStatus }}</h4>
    <div class="bar">
      <div :style="{width: barPercentage}" class="complition"></div>
    </div>
  </header>
</template>

<style scoped>
header {
  margin-top: 20px;
}

h4 {
  font-size: 30px;
  font-weight: 400;
}

.bar {
  width: 300px;
  height: 50px;
  border: 3px solid bisque;
}

.complition {
  height: 100%;
  width: 0%;
  background-color: bisque;
}
</style>
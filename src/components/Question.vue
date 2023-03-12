<script setup lang="ts">
  import { defineProps, defineEmits } from 'vue'

  const { question } = defineProps(['question'])
  const emit = defineEmits(['hendleOptionSelect'])

  const selectOption = (isCorrect: boolean): void => {
    emit('hendleOptionSelect', isCorrect)
  }
</script>

<template>
  <div class="question-container">
    <h1 class="question">
      {{ question.text }}
    </h1>
    <div class="options-container">
      <div 
        
        v-for="option in question.options" 
        :key="option.id" 
        @click="selectOption(option.isCorrect)"
        class="option"
      >
        <p class="option-label">{{ option.label }}</p>
        <p class="option-value">{{ option.text }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>

.options-container {
  display: flex;
  flex-direction: column;
  /* flex-wrap: wrap; */
  max-height: 300px;
  margin-top: 40px;
}
.question-container {
  margin-top: 20px;
}

.question {
  font-size: 40px;
  margin-bottom: 20px;
}

.option {
  display: flex;
  margin-bottom: 20px;
  cursor: pointer;
}

.option-label {
  background-color: bisque;
  width: 50px;
  height: 50px;
  font-size: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.option-value {
  background-color: rgb(244, 239, 239);
  width: 100%;
  font-size: 30px;
  padding: 0 20px;
}
</style>
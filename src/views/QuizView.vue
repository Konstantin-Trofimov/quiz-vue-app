<script setup lang="ts">
  import QuizHeader from '../components/QuizHeader.vue'
  import Question from '../components/Question.vue'
  import Result from '../components/Result.vue'

  import { ref, computed } from 'vue'
  import { useRoute } from 'vue-router'

  import quizes from '../assets/data.json'

  const route: any = useRoute()
  const quizId = parseInt(route.params.id)
  const quiz = quizes.find(q => q.id === quizId)
  const currentQuestionIndex: any = ref(0)
  const questionsLength: any = quiz?.questions.length
  const numberOfCorrectAnswers = ref(0)
  const showResult = ref(false)

  const questionStatus = computed(() => `${currentQuestionIndex.value}/${questionsLength}`)
  const barPercentage = computed(() => `${currentQuestionIndex.value / questionsLength * 100}%` ) 

  const onOptionSelected = (isCorrect: boolean) => {
    if (isCorrect) {
      numberOfCorrectAnswers.value++
    }

    if (questionsLength - 1 === currentQuestionIndex.value) {
      showResult.value = true
    }

    currentQuestionIndex.value++
  }
</script> 

<template>
  <QuizHeader 
    :questionStatus="questionStatus" 
    :barPercentage="barPercentage"
  />

  <Question 
    v-if="!showResult"
    @hendleOptionSelect="onOptionSelected"
    :question="quiz?.questions[currentQuestionIndex]"
  />

  <Result 
    v-else 
    :questionsLength="questionsLength"
    :numberOfCorrectAnswers="numberOfCorrectAnswers"
  />
</template>


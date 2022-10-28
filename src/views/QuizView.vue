<template>
  <div>
    <header>
      <h4>Question 1/3</h4>
      <div class="bar">
        <div class="completion"></div>
      </div>
    </header>
    <div>
      <Question :question="quiz.questions[currentQuestionIndex]" />
    </div>
  </div>
</template>

<script setup>
import Question from '../components/Question.vue';
import { useRoute } from 'vue-router';
import { ref } from 'vue';
import quizes from '../data/data.json';

const route = useRoute();
const quizId = parseInt(route.params.id);

// states
const currentQuestionIndex = ref(0);
const quiz = quizes.find((q) => q.id === quizId);
</script>

<script setup></script>

<style scoped>
header {
  margin-top: 20px;
}

header h4 {
  font-size: 30px;
}

.bar {
  width: 300px;
  height: 50px;
  border: 3px solid bisque;
}

.completion {
  height: 100%;
  width: 0%;
  background-color: bisque;
}
</style>

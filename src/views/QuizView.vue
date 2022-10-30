<template>
  <div>
    <header>
      <h4>Question {{ questionStatus }}</h4>
      <div class="bar">
        <div class="completion" :style="{ width: barProgress }"></div>
      </div>
    </header>
    <div>
      <Question
        :question="quiz.questions[currentQuestionIndex]"
        @selectOption="onUserSelect"
        v-if="!showResult"
      />
      <Result v-else :correctAnswers="correctAnswers" />
    </div>
  </div>
</template>

<script setup>
import Question from '../components/Question.vue';
import Result from '../components/Result.vue';
import { useRoute } from 'vue-router';
import { computed, ref, watch } from 'vue';
import quizes from '../data/data.json';

const route = useRoute();
const quizId = parseInt(route.params.id);

// states
const quiz = quizes.find((q) => q.id === quizId);
const currentQuestionIndex = ref(0);
const correctAnswers = ref(0);
const showResult = ref(false);

// computed properties
const questionStatus = computed(
  () => `${currentQuestionIndex.value}/ ${quiz.questions.length}`
);

const barProgress = computed(
  () => `${(currentQuestionIndex.value / quiz.questions.length) * 100}%`
);

// functions
const onUserSelect = (isCorrect) => {
  if (isCorrect) {
    correctAnswers.value++;
  }

  if (quiz.questions.length - 1 === currentQuestionIndex.value) {
    showResult.value = true;
  }
  currentQuestionIndex.value++;
};
</script>

<!--  -->

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

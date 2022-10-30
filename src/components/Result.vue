<template>
  <div class="result">
    <p>Your Result</p>
    <h4>Your score is {{ correctAnswers }}</h4>
    <RouterLink to="/">
      <button>Go home</button>
    </RouterLink>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';
import { RouterLink } from 'vue-router';

// states
const { correctAnswers } = defineProps(['correctAnswers']);
</script>

<style scoped>
.result {
  text-align: center;
  padding: 100px 0;
}

p {
  font-size: 25px;
}

h4 {
  font-size: 80px;
}
</style>

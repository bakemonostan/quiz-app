<template>
  <div class="card" @click="useNavigate">
    <img :src="quiz.img" alt="" />
    <div class="card-text">
      <h2>{{ quiz.name }}</h2>
      <p>{{ quiz.questions.length }}</p>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';
import { useRouter } from 'vue-router';

// states and routes
const { quiz } = defineProps(['quiz']);
const router = useRouter();

const useNavigate = () => {
  router.push(`/quiz/${quiz.id}`);
};
</script>

<style scoped></style>

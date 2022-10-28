<template>
  <div class="card">
    <img :src="quiz.img" alt="" />
    <div class="card-text">
      <h2>{{ quiz.name }}</h2>
      <p>{{ quiz.questions.length }}</p>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';
const { quiz } = defineProps(['quiz']);
</script>

<style scoped></style>

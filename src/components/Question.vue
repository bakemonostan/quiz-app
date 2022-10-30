<template>
  <div>
    <div class="question-container">
      <h5 class="question">{{ question.text }}</h5>
    </div>
    <div class="options-container">
      <div
        @click="userOption(option.isCorrect)"
        class="option"
        v-for="option in question.options"
        :key="option.id"
      >
        <p class="option-label">{{ option.label }}</p>
        <div class="option-value">
          <p>{{ option.text }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const emit = defineEmits(['selectOption']);
const { question } = defineProps(['question']);
const userOption = (isCorrect) => {
  emit('selectOption', isCorrect);
};
</script>

<style scoped>
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
  width: 100%;
  padding: 0 20px;
  background-color: rgb(244, 239, 239);
  font-size: 30px;
}
</style>

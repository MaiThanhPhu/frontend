<template>
  <div class="question-display">
    <div class="answers">
        <button class="answer a"></button>
        <button class="answer b"></button>
        <button class="answer c"></button>
        <button class="answer d"></button>
</div>
  </div>
</template>

<script setup>
import { useRoute } from 'vue-router'
const route = useRoute()
const roomId = route.params.roomId
</script>

<style scoped>
.question-display {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 40px 20px;
  min-height: 100vh;
  background: linear-gradient(135deg, #fdfcfb, #e2d1c3);
  font-family: 'Segoe UI', sans-serif;
}

.header {
  width: 100%;
  text-align: right;
  font-size: 20px;
  margin-bottom: 30px;
  padding-right: 40px;
  color: #4a148c;
}

.question-box {
  background: #6a1b9a;
  color: white;
  padding: 500px;
  border-radius: 16px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.2);
  text-align: center;
  width: 80%;
  margin-bottom: 40px;
}

.question {
  font-size: 28px;
  margin: 0;
}

.answers {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 50px;
  max-width: 500px;
  margin: 500;
}

.answer {
  padding: 20px 40px;
  border: none;
  font-size: 24px;
  font-weight: bold;
  color: #fff;
  border-radius: 16px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.a {
  background-color: #4CAF50; /* xanh lá */
  padding: 90px 100px;
}

.b {
  background-color: #F44336; /* đỏ */
  padding: 90px 100px;
}

.c {
  background-color: #FF9800; /* cam */
  padding: 90px 100px;
}

.d {
  background-color: #9C27B0; /* tím */
  padding: 90px 100px;
}

.answer:hover {
  transform: scale(1.05);
  opacity: 0.9;
}
</style>

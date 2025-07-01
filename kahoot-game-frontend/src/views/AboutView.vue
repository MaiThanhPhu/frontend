<template>
  <div class="dashboard-container">
    <h1>Chào mừng trở lại, {{ username }}!</h1>
    <p>Bạn đã sẵn sàng để bắt đầu một trò chơi Kahoot?</p>

    <div class="dashboard-actions">
      <router-link to="/create-game" class="action-button primary">Tạo Game Mới</router-link>
      <router-link to="/join-game" class="action-button secondary">Tham Gia Game</router-link>
    </div>

    <div class="info-section">
      <p>Tại đây, bạn có thể quản lý các game của mình hoặc khám phá các game mới.</p>
      </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const username = ref('Bạn'); // Giá trị mặc định nếu không lấy được tên người dùng

onMounted(() => {
  // Lấy email người dùng từ Local Storage để hiển thị tên
  const userEmail = localStorage.getItem('userEmail'); 
  if (userEmail) {
    // Lấy phần tên trước ký tự '@' để làm tên hiển thị
    username.value = userEmail.split('@')[0]; 
  }
});
</script>

<style scoped>
.dashboard-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: calc(100vh - 60px); /* Trừ chiều cao header nếu có */
  background: linear-gradient(135deg, #fdfcfb 0%, #e2d1c3 100%); /* Nền nhẹ nhàng */
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #333;
  padding: 40px 20px;
  box-sizing: border-box;
}

h1 {
  font-size: 3.5em;
  color: #4a148c; /* Màu tím đậm của Kahoot */
  margin-bottom: 20px;
  text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
}

p {
  font-size: 1.4em;
  color: #555;
  margin-bottom: 40px;
  max-width: 700px;
  text-align: center;
  line-height: 1.5;
}

.dashboard-actions {
  display: flex;
  gap: 30px;
  margin-bottom: 50px;
}

.action-button {
  display: inline-block;
  padding: 18px 40px;
  font-size: 1.6em;
  font-weight: bold;
  border-radius: 12px;
  text-decoration: none;
  transition: all 0.3s ease;
  box-shadow: 0 6px 15px rgba(0,0,0,0.2);
  min-width: 250px;
  text-align: center;
}

.action-button.primary {
  background-color: #6a1b9a; /* Màu tím Kahoot */
  color: white;
  border: 2px solid #6a1b9a;
}

.action-button.primary:hover {
  background-color: #4a148c;
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0,0,0,0.3);
}

.action-button.secondary {
  background-color: white;
  color: #6a1b9a;
  border: 2px solid #6a1b9a;
}

.action-button.secondary:hover {
  background-color: #f0f0f0;
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0,0,0,0.3);
}

.info-section {
  margin-top: 30px;
  padding: 25px;
  background-color: rgba(255, 255, 255, 0.8);
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.08);
}

.info-section p {
  margin: 0;
  font-size: 1.1em;
  color: #666;
}
</style>
<template>
  <div class="home">
    <h1>Chào mừng bạn đến với Kahoot Game!</h1>
    <p>Hãy đăng nhập hoặc đăng ký để bắt đầu chơi.</p>
    <div class="navigation-links">
      <router-link to="/login">Đăng nhập</router-link>
      <router-link to="/register">Đăng ký</router-link>
    </div>
  </div>
</template>
<style scoped>
.home { text-align: center; padding: 50px; }

.navigation-links {
  background-color: #2c3e50; /* Màu nền thanh nav */
  padding: 15px 0;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 30px;
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 999;
}

.navigation-links a {
  color: #ecf0f1;
  text-decoration: none;
  font-weight: bold;
  padding: 10px 20px;
  border-radius: 8px;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

.navigation-links a:hover {
  background-color: #3498db;
  transform: translateY(-2px);
}

.navigation-links a.router-link-exact-active {
  background-color: #1abc9c;
}

</style>
<template>
  <div id="app">
    <header>
      <nav class="navigation-links" > 
        
        <router-link to="/login">Đăng nhập</router-link>
        <router-link to="/register">Đăng ký</router-link>
        <router-link to="/">Đăng xuất</router-link>
      </nav>
    </header>
    <main>
      <router-view />
    </main>
  </div>
</template>

<script setup>
// Không cần import hay sử dụng component nào ở đây nữa nếu đã xóa TheWelcome.vue
</script>

<style>
/* Global styles */
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f4f4f4;
}

#app {
  /* Loại bỏ hoặc ghi đè các style mặc định của Vite/Vue */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #5486c7;
  min-height: 100vh; /* Đảm bảo app chiếm toàn bộ chiều cao màn hình */
  display: flex;
  flex-direction: column;
}

header {
  background-color: #333;
  padding: 15px 0;
  text-align: center;
}

nav {
  display: flex; /* Sử dụng flexbox để căn giữa hoặc phân bố các link */
  justify-content: center; /* Căn giữa các link */
  align-items: center;
}

nav a {
  font-weight: bold;
  color: #c20d0d;
  text-decoration: none;
  margin: 0 15px;
  padding: 5px 10px; /* Thêm padding để dễ bấm */
  border-radius: 4px;
  transition: background-color 0.3s ease;
}

nav a:hover {
  background-color: #555555;
}

nav a.router-link-exact-active {
  color: #42b983; /* Màu xanh lá nổi bật cho link đang active */
  background-color: #555; /* Nền tối hơn một chút khi active */
}

main {
  flex-grow: 1; /* Cho phép main chiếm không gian còn lại */
  padding: 20px;
  display: flex; /* Để căn giữa nội dung của từng trang con */
  justify-content: center;
  align-items: flex-start; /* Căn trên đầu trang */
}

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
  background-color: #0b79e0;
}
</style>
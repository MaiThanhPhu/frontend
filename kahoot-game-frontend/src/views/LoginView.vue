<template>
  <div class="auth-page">
    <h2>Đăng nhập</h2>
    <form @submit.prevent="handleLogin">
      <div class="form-group">
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="email" required>
      </div>
      <div class="form-group">
        <label for="password">Mật khẩu:</label>
        <input type="password" id="password" v-model="password" required>
      </div>
      <button type="submit">Đăng nhập</button>
      <p v-if="error" class="error-message">{{ error }}</p>
    </form>
    <p>Chưa có tài khoản? <router-link to="/register">Đăng ký ngay!</router-link></p>
  </div>
</template>
<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import axios from 'axios';

// Lấy URL cơ sở của API từ biến môi trường
const API_BASE_URL = import.meta.env.VITE_API_BASE_URL; 
const email = ref('');
const password = ref('');
const error = ref(null);
const router = useRouter();

const handleLogin = async () => {
  error.value = null;
  try {
    const response = await axios.post(`${API_BASE_URL}/api/auth/login`, {
      email: email.value,
      password: password.value
    });
    localStorage.setItem('userToken', response.data.token);
    localStorage.setItem('userInfo', JSON.stringify({
      _id: response.data._id,
      username: response.data.username,
      email: response.data.email
    }));
    alert('Đăng nhập thành công!');
    router.push('/dashboard');
  } catch (err) {
    console.error('Lỗi đăng nhập:', err.response ? err.response.data : err.message);
    error.value = err.response && err.response.data.message
                  ? err.response.data.message
                  : 'Đăng nhập thất bại. Vui lòng thử lại.';
  }
};
</script>
<style scoped>
.auth-page { max-width: 400px; margin: 50px auto; padding: 20px; border: 1px solid #ccc; border-radius: 8px; box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); text-align: center; }
.form-group { margin-bottom: 15px; text-align: left; }
.form-group label { display: block; margin-bottom: 5px; font-weight: bold; }
.form-group input { width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 4px; }
button { background-color: #07be44; color: white; padding: 10px 15px; border: none; border-radius: 4px; cursor: pointer; font-size: 16px; }
button:hover { background-color: #b811b8; }
.error-message { color: red; margin-top: 10px; }
</style>
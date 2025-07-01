<template>
  <div class="auth-page">
    <h2>Đăng ký tài khoản mới</h2>
    <form @submit.prevent="handleRegister">
      <div class="form-group">
        <label for="newUsername">Tên đăng nhập:</label>
        <input type="text" id="newUsername" v-model="newUsername" required>
      </div>
      <div class="form-group">
        <label for="newEmail">Email:</label>
        <input type="email" id="newEmail" v-model="newEmail" required>
      </div>
      <div class="form-group">
        <label for="newPassword">Mật khẩu:</label>
        <input type="password" id="newPassword" v-model="newPassword" required>
      </div>
      <div class="form-group">
        <label for="confirmPassword">Xác nhận mật khẩu:</label>
        <input type="password" id="confirmPassword" v-model="confirmPassword" required>
      </div>
      <button type="submit">Đăng ký</button>
      <p v-if="error" class="error-message">{{ error }}</p>
    </form>
    <p>Đã có tài khoản? <router-link to="/login">Đăng nhập ngay!</router-link></p>
  </div>
</template>
<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import axios from 'axios';

const newUsername = ref('');
const newEmail = ref('');
const newPassword = ref('');
const confirmPassword = ref('');
const error = ref(null);
const router = useRouter();

const handleRegister = async () => {
  error.value = null;
  if (newPassword.value !== confirmPassword.value) {
    error.value = 'Mật khẩu xác nhận không khớp!';
    return;
  }
  try {
    const response = await axios.post('http://localhost:5000/api/auth/register', {
      username: newUsername.value,
      email: newEmail.value,
      password: newPassword.value
    });
    alert('Đăng ký thành công! Vui lòng đăng nhập.');
    router.push('/login');
  } catch (err) {
    console.error('Lỗi đăng ký:', err.response ? err.response.data : err.message);
    error.value = err.response && err.response.data.message
                  ? err.response.data.message
                  : 'Đăng ký thất bại. Vui lòng thử lại.';
  }
};
</script>
<style scoped>
.auth-page { max-width: 400px; margin: 50px auto; padding: 20px; border: 1px solid #ccc; border-radius: 8px; box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); text-align: center; }
.form-group { margin-bottom: 15px; text-align: left; }
.form-group label { display: block; margin-bottom: 5px; font-weight: bold; }
.form-group input { width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 4px; }
button { background-color: #07be44; color: white; padding: 10px 15px; border: none; border-radius: 4px; cursor: pointer; font-size: 16px; }
button:hover { background-color: #2114d4; }
.error-message { color: red; margin-top: 10px; }
</style>
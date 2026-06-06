<template>
  <div class="main-wrapper">
    <div class="info-section">
      <img :src="base + 'moodle4_log.jpg'" alt="iLearn Logo" class="logo-image" />

      <div class="announcement">
        <p>● 系統維護時間:每週八1:00-3:00</p>
        <p>● 帳號請使用逢甲大學 NID</p>
      </div>
    </div>

    <div class="login-card">
      <h3>使用者登入</h3>
      <form @submit.prevent="onSubmit">
        <input v-model="username" type="text" id="username" placeholder="帳號" required />
        <input v-model="password" type="password" id="password" placeholder="密碼" required />

        <div class="options">
          <label><input v-model="remember" type="checkbox" /> 記住帳號</label>
        </div>

        <button :disabled="loading" type="submit" class="login-btn">{{ loading ? '處理中...' : '登入' }}</button>
      </form>

      <div class="footer-links">
        <a href="#">忘記密碼？</a>
        <a href="#">常見問題</a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const username = ref('')
const password = ref('')
const remember = ref(false)
const loading = ref(false)

// Use BASE_URL so public assets respect `base` in vite.config.js
const base = import.meta.env.BASE_URL || '/'

function onSubmit() {
  loading.value = true

  setTimeout(() => {
    alert(`你好 ${username.value}，登入模擬完成。`)
    loading.value = false
  }, 800)
}
</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: "Segoe UI", "Microsoft JhengHei", sans-serif;
}

.main-wrapper {
  display: flex;
  flex-direction: row;
  width: 90%;
  max-width: 900px;
  gap: 40px;
  align-items: center;
  margin: 40px auto;
}

.info-section {
  flex: 1;
}

.logo-image {
  max-width: 350px;
  height: auto;
  margin-bottom: 20px;
}

.announcement {
  margin-top: 20px;
  color: #555;
  line-height: 1.8;
}

.login-card {
  flex: 0 0 350px;
  background: #fff;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.1);
}

.login-card h3 {
  margin-bottom: 20px;
  color: #333;
  border-left: 5px solid #005596;
  padding-left: 10px;
}

input[type="text"], input[type="password"] {
  width: 100%;
  padding: 12px;
  margin-bottom: 15px;
  border: 1px solid #ddd;
  border-radius: 6px;
  font-size: 1rem;
}

.options {
  margin-bottom: 15px;
  font-size: 0.9rem;
  color: #666;
}

.login-btn {
  width: 100%;
  padding: 12px;
  background: #005596;
  color: white;
  border: none;
  border-radius: 6px;
  font-size: 1.1rem;
  cursor: pointer;
}

.login-btn:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.login-btn:hover:not(:disabled) {
  background: #00447a;
}

.footer-links {
  margin-top: 20px;
  display: flex;
  justify-content: space-between;
  font-size: 0.85rem;
}

.footer-links a {
  color: #005596;
  text-decoration: none;
}

@media (max-width: 768px) {
  .main-wrapper {
    flex-direction: column;
    text-align: center;
  }
  .info-section {
    margin-bottom: 20px;
  }
  .logo-image {
    max-width: 250px;
  }
  .login-card {
    width: 100%;
    flex: none;
  }
}
</style>

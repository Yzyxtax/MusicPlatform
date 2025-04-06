<template>
    <div class="auth-container">
      <div class="card">
        <h2>{{ isLoginMode ? '登录' : '注册' }}</h2>
        
        <form @submit.prevent="handleSubmit">
          <div class="form-group">
            <label>手机号</label>
            <input 
              type="tel" 
              v-model="formData.phone" 
              required
              placeholder="请输入11位手机号"
              pattern="^1[3-9]\d{9}$"
            >
          </div>
  
          <div class="form-group">
            <label>密码</label>
            <input
              type="password"
              v-model="formData.password"
              required
              placeholder="请输入密码"
              minlength="6"
            >
          </div>
  
          <div class="form-group" v-if="!isLoginMode">
            <label>确认密码</label>
            <input
              type="password"
              v-model="formData.confirmPassword"
              required
              placeholder="请再次输入密码"
              minlength="6"
            >
          </div>
  
          <div class="error-message" v-if="errorMessage">{{ errorMessage }}</div>
  
          <button type="submit" :disabled="isLoading">
            {{ isLoading ? '提交中...' : isLoginMode ? '登录' : '注册' }}
          </button>
        </form>
  
        <div class="toggle-mode">
          {{ isLoginMode ? '没有账号？' : '已有账号？' }}
          <a href="#" @click.prevent="toggleMode">{{ isLoginMode ? '立即注册' : '立即登录' }}</a>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
import { ref, reactive } from 'vue'

const isLoginMode = ref(true)
const isLoading = ref(false)
const errorMessage = ref('')

const formData = reactive({
  phone: '',
  password: '',
  confirmPassword: ''
})

const validateForm = () => {
  const phonePattern = /^1[3-9]\d{9}$/
  
  // 手机号验证
  if (!formData.phone) {
    return '请输入手机号'
  }
  if (!phonePattern.test(formData.phone)) {
    return '请输入有效的11位手机号'
  }

  // 密码验证
  if (!formData.password) {
    return '请输入密码'
  }
  
  // 注册模式下的确认密码验证
  if (!isLoginMode.value) {
    if (formData.password !== formData.confirmPassword) {
      return '两次输入的密码不一致'
    }
  }

  return null // 必须返回null表示验证通过
}

const handleSubmit = async () => {
  const validationError = validateForm()
  if (validationError) {
    errorMessage.value = validationError
    return
  }

  try {
    isLoading.value = true
    errorMessage.value = ''
    
    // 模拟API调用
    await new Promise(resolve => setTimeout(resolve, 1500))
    
    // 这里可以添加实际的API调用
    if (isLoginMode.value) {
      console.log('执行登录操作', formData)
    } else {
      console.log('执行注册操作', formData)
    }
    
  } catch (error) {
    errorMessage.value = '请求失败，请稍后重试'
  } finally {
    isLoading.value = false
  }
}

const toggleMode = () => {
  isLoginMode.value = !isLoginMode.value
  errorMessage.value = ''
  // 重置确认密码字段（仅在切换到登录模式时清空）
  if (isLoginMode.value) {
    formData.confirmPassword = ''
  }
}
</script>
  
  <style scoped>
  .auth-container {
    max-width: 400px;
    margin: 2rem auto;
    padding: 20px;
  }
  
  .card {
    background: #fff;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  }
  
  h2 {
    text-align: center;
    color: #333;
    margin-bottom: 1.5rem;
  }
  
  .form-group {
    margin-bottom: 1rem;
  }
  
  label {
    display: block;
    margin-bottom: 0.5rem;
    color: #666;
  }
  
  input {
    width: 100%;
    padding: 0.5rem;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 1rem;
  }
  
  button {
    width: 100%;
    padding: 0.75rem;
    background: #007bff;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 1rem;
  }
  
  button:disabled {
    background: #ccc;
    cursor: not-allowed;
  }
  
  .toggle-mode {
    text-align: center;
    margin-top: 1rem;
    color: #666;
  }
  
  a {
    color: #007bff;
    text-decoration: none;
  }
  
  .error-message {
    color: #dc3545;
    margin-bottom: 1rem;
    text-align: center;
  }
  </style>
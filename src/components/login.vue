<script setup>

import axios from 'axios';
import { ref,onMounted } from 'vue';



const phone_number = ref('');
const password = ref('');

const login={
    phone_number:phone_number,
    password:password
}

const enroll=async()=>{
   try {
      const userInfo = {
         phone_number: phone_number.value,
         password:password.value
      }; // 获取 注册信息 
      const url = `http://localhost:8081/users`;  
      const response = await axios.post(url,userInfo,{
         headers: {
            "Content-Type": "application/json"
         }
      });  
      console.log('添加用户信息响应', response.data); 
   } catch (error) {
      console.error("出错", error);  
      alert("加载失败，请稍后再试。"); // 友好的错误提示  
   }
}

onMounted(() => {
    enroll();
});
</script>

<template>
    
</template>

<style scoped>
</style>
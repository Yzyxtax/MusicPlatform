<script setup>
import axios from 'axios';
import { ref,onMounted } from 'vue';



const fetchPosts=async()=>{
   try {
      const userAccount = 1; // 获取帖子 ID  
      const url = `http://localhost:8081/users/${userAccount}`; // 拼接 URL  
      const response = await axios.get(url);  
      //    post.value = response.data;
      console.log('响应', response.data); 

      console.log(response.data[0].is_certified_singer); // 正确字段名应为后端返回的实际名称
      
   } catch (error) {
      console.error("出错", error);  
      alert("加载失败，请稍后再试。"); // 友好的错误提示  
   }
}
onMounted(() => {
    fetchPosts();
});


const fetchPosts2=async()=>{
   try {
      const songId = 1; // 获取帖子 ID  
      const url = `http://localhost:8081/songs/${songId}`; // 拼接 URL  
      const response = await axios.get(url);  
      //    post.value = response.data;
      console.log('响应', response.data); 
   } catch (error) {
      console.error("出错", error);  
      alert("加载失败，请稍后再试。"); // 友好的错误提示  
   }
}
onMounted(() => {
    fetchPosts2();
});
</script>

<template>

</template>
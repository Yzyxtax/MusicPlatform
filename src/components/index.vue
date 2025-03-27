<script setup>
import axios from 'axios';
import { ref,onMounted } from 'vue';



const fetchPosts=async()=>{

try {
  
 const user_account = 1; // 获取帖子 ID  
  const url = `http://localhost:8081/users/${user_account}`; // 拼接 URL  
  const response = await axios.get(url);  

//    post.value = response.data;
   console.log('响应', response.data); 


} catch (error) {
   console.error("出错", error);  
  alert("加载失败，请稍后再试。"); // 友好的错误提示  
  
}


}
onMounted(() => {
    fetchPosts();
});
</script>

<template>

</template>
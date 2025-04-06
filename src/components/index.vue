<script setup>
import axios from 'axios';
import { ref,onMounted } from 'vue';



const fetchPosts=async()=>{
   try {
      const userAccount = 1; // 获取 ID  
      const url = `http://localhost:8081/users/${userAccount}`; // 拼接 URL  
      const response = await axios.get(url);  
      //    post.value = response.data;
      console.log('查询用户信息响应', response.data); 
   } catch (error) {
      console.error("出错", error);  
      alert("加载失败，请稍后再试。"); // 友好的错误提示  
   }
}

const fetchPosts2=async()=>{
   try {
      const songId = 1; // 获取 ID  
      const url = `http://localhost:8081/songs/${songId}`; // 拼接 URL  
      const response = await axios.get(url);  
      //    post.value = response.data;
      console.log('查询歌曲信息响应', response.data); 
   } catch (error) {
      console.error("出错", error);  
      alert("加载失败，请稍后再试。"); // 友好的错误提示  
   }
}

const fetchPosts3=async()=>{
   try {
      const userAccount = 1; // 获取 ID  
      const url = `http://localhost:8081/userFollowList/${userAccount}`; // 拼接 URL  
      const response = await axios.get(url);  
      console.log('查询关注列表响应', response.data); 
   } catch (error) {
      console.error("出错", error);  
      alert("加载失败，请稍后再试。"); // 友好的错误提示  
   }
}

const fetchPosts4=async()=>{
   try {
      const userAccount = 1; // 获取 ID  
      const url = `http://localhost:8081/songPurcheases/${userAccount}`; // 拼接 URL  
      const response = await axios.get(url);  
      console.log('查询购买歌曲信息响应', response.data); 
   } catch (error) {
      console.error("出错", error);  
      alert("加载失败，请稍后再试。"); // 友好的错误提示  
   }
}

const fetchPosts5=async()=>{
   try {
      const userAccount = 1; // 获取 ID  
      const url = `http://localhost:8081/playListSummary/${userAccount}`; // 拼接 URL  
      const response = await axios.get(url);  
      console.log('查询用户创建歌单响应', response.data); 
   } catch (error) {
      console.error("出错", error);  
      alert("加载失败，请稍后再试。"); // 友好的错误提示  
   }
}

const fetchPosts6=async()=>{
   try {
      const playListId = 1; // 获取 ID  
      const url = `http://localhost:8081/playList/${playListId}`; // 拼接 URL  
      const response = await axios.get(url);  
      console.log('查询歌单歌曲信息响应', response.data); 
   } catch (error) {
      console.error("出错", error);  
      alert("加载失败，请稍后再试。"); // 友好的错误提示  
   }
}

const fetchPosts7=async()=>{
   try {
      const userAccount = 1; // 获取 ID  
      const url = `http://localhost:8081/favoritePlayList/${userAccount}`; // 拼接 URL  
      const response = await axios.get(url);  
      console.log('查询收藏歌单信息响应', response.data); 
   } catch (error) {
      console.error("出错", error);  
      alert("加载失败，请稍后再试。"); // 友好的错误提示  
   }
}




const enroll=async()=>{
   try {
      const userInfo = {
         phone_number:'23456789101',
         password:'12345678'
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

const Modify=async()=>{
   try {
      const userInfo = {
         user_account:4,
         nickname:'yzy',
         password:'87654321',
         signature:'喜欢下课',
         name:'小明',
         identification_number:'123456789012345678',
         gender:'男',
         is_cretified_singer:true,
         is_member:true,
         birth_date:'1990-01-01',
         phone_number:'13512345678',
      }; // 获取 修改信息 
      const url = `http://localhost:8081/users`;
      const response = await axios.put(url,userInfo,{
         headers: {
            "Content-Type": "application/json"
         }
      });  
      console.log('修改用户信息响应', response.data); 
   } catch (error) {
      console.error("出错", error);  
      alert("加载失败，请稍后再试。"); // 友好的错误提示  
   }
}

const deleteUser=async()=>{
   try {
      const userAccount = 6 // 获取 ID信息 
      const url = `http://localhost:8081/users/${userAccount}`; // 拼接 URL  
      const response = await axios.delete(url);  
      console.log('删除用户信息响应', response.data); 
   } catch (error) {
      console.error("出错", error);  
      alert("加载失败，请稍后再试。"); // 友好的错误提示  
   }
}

const deleteUser2=async()=>{
   try {
      const userInfo = {
         phone_number:'13755499157',
         password:'2580147Xx'
      }; // 获取 注册信息 
      const url = `http://localhost:8081/users/login`;  
      const response = await axios.post(url,userInfo,{
         headers: {
            "Content-Type": "application/json"
         }
      });  
      console.log('登陆用户响应', response.data); 
   } catch (error) {
      console.error("出错", error);  
      alert("加载失败，请稍后再试。"); // 友好的错误提示  
   }
}



onMounted(() => {
   //fetchPosts();

   // fetchPosts2();
   // fetchPosts3();
   // fetchPosts4();
   // fetchPosts5();
   // fetchPosts6();
   // fetchPosts7();

   //   enroll();
   // Modify();
   //deleteUser();
   deleteUser2();
});
</script>

<template>

</template>
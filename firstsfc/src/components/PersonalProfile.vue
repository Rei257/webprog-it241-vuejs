<template>
  <div class="app">

    <nav class="navbar">
      <a href="#" @click.prevent="page='home'" class="nav-btn">Home</a>
      <a href="#" @click.prevent="page='about'" class="nav-btn">About Me</a>
    </nav>

    <div v-if="page==='home'">
      <div class="photo-booth left">
        <img v-for="(img,i) in boothImages" :key="'l'+i" :src="img" class="booth-img" @click="zoomImage=img">
      </div>

      <div class="photo-booth right">
        <img v-for="(img,i) in boothImages" :key="'r'+i" :src="img" class="booth-img" @click="zoomImage=img">
      </div>

      <section class="landing">
        <img :src="profilePic" id="profile-pic" @click="zoomImage=profilePic">
        <h2>John Carl Gabriel Guzman</h2>
        <p class="subtitle">BSIT • Web Programming (IT241)</p>
      </section>
    </div>

    <div v-else class="grid-container">
      <div class="custom-box" v-for="box in boxes" :key="box.title">
        <h3>{{ box.title }}</h3>
        <p v-html="box.content"></p>
      </div>
    </div>

    <div v-if="zoomImage" class="modal" @click.self="zoomImage=null">
      <img :src="zoomImage">
    </div>

    <footer class="footer">
      © 2026 APC Web Programming
    </footer>

  </div>
</template>

<script setup>
import { ref } from 'vue'

import jc from '@/Images/JC.jpg'
import family from '@/Images/Family.jpg'
import gala from '@/Images/Gala.jpg'
import friends from '@/Images/Friends.jpg'

const page = ref('home')
const zoomImage = ref(null)

const boothImages = [jc, family, gala, friends]
const profilePic = jc

const boxes = [
  { title: "About Me", content: "Calm, quiet. I enjoy watching movies and anime." },
  { title: "Education", content: "Asia Pacific College<br>2nd Year BSIT" },
  { title: "Course", content: "Web Programming (IT241)" },
  { title: "IT Experience", content: "Kali Linux<br>Python<br>Ubuntu<br>HTML & CSS" },
  { title: "Hobbies & Interests", content: "Music<br>Manga & Manhwa<br>Anime<br>Movies" },
  { title: "Goals / Dreams", content: "To become financially successful and travel around the world." }
]
</script>

<style scoped>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family: 'Noto Sans Mono', monospace;
}

.navbar{
  background:black;
  padding:12px;
  text-align:center;
}
.nav-btn{
  color:white;
  margin:0 15px;
  text-decoration:none;
  font-weight:bold;
}
.nav-btn:hover{
  color:#00bcd4;
}

.photo-booth{
  position:fixed;
  top:80px;
  width:120px;
  display:flex;
  flex-direction:column;
  gap:10px;
}
.left{ left:10px; }
.right{ right:10px; }

.booth-img{
  width:100%;
  cursor:pointer;
  border-radius:8px;
  transition:0.3s;
}
.booth-img:hover{
  transform:scale(1.1);
}

.landing{
  min-height:90vh;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  text-align:center;
}
#profile-pic{
  width:220px;
  height:220px;
  border-radius:50%;
  object-fit:cover;
  cursor:pointer;
  box-shadow:0 10px 25px rgba(0,0,0,0.3);
}
.subtitle{ color:gray; }

.grid-container{
  padding:80px 40px;
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
  gap:20px;
}
.custom-box{
  background:#111;
  color:white;
  padding:20px;
  border-radius:10px;
  text-align:center;
}

.modal{
  position:fixed;
  inset:0;
  background:rgba(0,0,0,0.8);
  display:flex;
  justify-content:center;
  align-items:center;
}
.modal img{
  max-width:80%;
  max-height:80%;
}

.footer{
  text-align:center;
  padding:20px;
  background:black;
  color:white;
}
</style>

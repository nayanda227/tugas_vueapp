<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.png" width="50" height="50" />
    <h1>Vue App by Nadia</h1>
  </header>

  <main>
    <section class="click-counter">
        <div class="section-box">
        <h2>Click Counter</h2>
        <div class="counter-number">{{ counter }}</div> 
        <button class="primary-btn" @click="incrementCounter">
        Click to Count 
      </button>
      </div>
    </section>

    <section class="box-changer">
      <div class="section-box">
        <h2>Box Color Changer</h2>
        <div :style="boxStyle" @click="changeColor" class="color-box">{{ colors[currentColorIndex] }}</div>
      </div>
    </section>

    <section class="image-carousel">
      <h2>Image Carousel</h2>
      <div class="section-box full-carousel">
        <div class="carousel">
          <button class="carousel-nav left" @click="prevImage">&lt;</button>
          <img :src="images[currentImage]" alt="carousel image" />
          <button class="carousel-nav right" @click="nextImage">&gt;</button>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
import { ref, computed } from 'vue'

// Click Counter
const counter = ref(0)
const incrementCounter = () => {
  counter.value++
}

// Box Color Changer
const colors = ["#FF5733", "#28A745", "#007BFF", "#FFC107", "#6F42C1", "#F7CAC9", "#92A8D1", "#C8102E", "#C0C0C0", "#39FF14", "#7FDBFF", "#FF6F61", "#6D28D9"]
const currentColorIndex = ref(0)
const changeColor = () => {
  currentColorIndex.value = (currentColorIndex.value + 1) % colors.length
}
const boxStyle = computed(() => ({
  width: '200px',
  height: '200px',
  borderRadius: '20px',
  backgroundColor: `${colors[currentColorIndex.value]}B3`, // Transparansi 70%
  boxShadow: '0 8px 16px rgba(0, 0, 0, 0.1)',
  display: 'flex',
  alignItems: 'center',
  justifyContent: 'center',
  color: '#333', // Kontras dengan background
  fontSize: '1.5rem',
  fontWeight: 'bold',
  transition: 'background-color 0.5s ease, transform 0.3s ease',
  cursor: 'pointer',
}))
// Image Carousel
const currentImage = ref(0)
const images = [
  require('./assets/image1.png'),
  require('./assets/image2.png'),
  require('./assets/image3.jpg'),
]
const nextImage = () => {
  currentImage.value = (currentImage.value + 1) % images.length
}
const prevImage = () => {
  currentImage.value = (currentImage.value - 1 + images.length) % images.length
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif; 
  background:  url('./assets/wood_texture.jpeg') no-repeat center center fixed; /* Gambar kayu putih */
  background-size: cover;
  color: #333;
  transition: background 0.5s ease;
}

header {
  display: flex;
  align-items: center;
  padding: 1rem;
}

.logo {
  margin-right: 1rem;
}

h1 {
  font-size: 2rem;
  color: #010911;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.1);
}

main {
  max-width: 900px;
  margin: 0 auto;
  padding: 2rem;
}

section {
  margin-bottom: 3rem;
  text-align: center;
}

.section-box {
  padding: 2rem;
  background: rgba(255, 255, 255, 0.4); /* Transparansi box */
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
  border-radius: 16px;
  margin-top: 1rem;
  transition: transform 0.3s ease;
}

.section-box:hover {
  transform: translateY(-5px);
}
.counter-number {
  font-size: 2.5rem; /* Ukuran angka lebih kecil */
  font-weight: bold;
  color: #4371c2; 
  margin-bottom: 0.5rem; /* Kurangi jarak antara angka dan tombol */
}

.primary-btn {
  padding: 12px 30px;
  font-size: 1.2rem;
  border: none;
  cursor: pointer;
  border-radius: 10px;
  background-color: #4371c2;
  color: #fff;
  transition: background-color 0.3s ease, transform 0.2s ease;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
}

.primary-btn:hover {
  background-color: #42838b;
  transform: translateY(-2px);
}

.color-box {
  margin: 20px auto;
  width: 200px;
  height: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: transform 0.3s ease;
}

.color-box:hover {
  transform: scale(1.1);
}

.full-carousel {
  position: relative;
  padding: 0;
  background: transparent;
}

.carousel img {
  width: 100%;
  max-width: 100%;
  height: auto;
  border-radius: 12px;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
  transition: opacity 0.5s ease;
}

.carousel img:hover {
  opacity: 0.9;
}

.carousel-nav {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(0, 0, 0, 0.5);
  border: none;
  color: white;
  font-size: 2rem;
  padding: 0.5rem;
  cursor: pointer;
  z-index: 10;
}

.carousel-nav.left {
  left: 0;
}

.carousel-nav.right {
  right: 0;
}
</style>

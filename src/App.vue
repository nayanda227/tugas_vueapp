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
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

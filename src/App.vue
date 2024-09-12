<template>
  <div id="app">

  <div class="container">
    <!-- Click Counter Section -->
    <div class="counter-section">
      <h2>Click Counter</h2>
      <p class="counter-display">Counter: {{ counter }}</p>
      <button class="btn" @click="increaseCounter">Increase Counter</button>
    </div>

    <!-- Box Color Changer Section -->
    <div class="color-changer-section">
      <h2>Box Color Changer</h2>
      <div class="color-box" :style="{ backgroundColor: currentColor }"></div>
      <button class="btn" @click="changeColor">Change Color</button>
    </div>

    <!-- Image Carousel Section -->
    <div class="carousel-section">
      <h2>Image Carousel</h2>
      <div class="carousel">
        <transition name="fade" mode="out-in">
          <img :key="currentImage" :src="images[currentImage]" alt="carousel image" />
        </transition>
      </div>
          <button class="btn" @click="prevImage">Previous</button>
          <button class="btn" @click="nextImage">Next</button>
        </div>
      </div>
  </div>    
</template>

<script setup>
import { ref } from 'vue';

// Click Counter
const counter = ref(0);
const increaseCounter = () => {
  counter.value++;
};

// Box Color Changer
const colors = ['#4379F2', '#FFEB00', '#6EC207', '#C7253E', '#37B7C3', '#FF4191'];
const currentColor = ref(colors[0]);
const changeColor = () => {
  const randomIndex = Math.floor(Math.random() * colors.length);
  currentColor.value = colors[randomIndex];
};

// Image Carousel
const images = [
  'img/img1.jpg',
  'img/img2.jpg',
  'img/img3.jpg',
  'img/img4.jpg',
  'img/img5.jpg',
  'img/img6.jpg'
];
const currentImage = ref(0);
const nextImage = () => {
  currentImage.value = (currentImage.value + 1) % images.length;
};
const prevImage = () => {
  currentImage.value = (currentImage.value - 1 + images.length) % images.length;
};
</script>

<style scoped>

body {
  background-color: #dec1ff;
  margin: 0;
  height: 100vh; /* Pastikan tinggi penuh untuk body */
  display: flex;
  justify-content: center;
  align-items: center;

}

#app {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  text-align: center;
  max-width: 600px;
  padding: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
  /* margin-left: 50%; */
  background-color: #dec1ff;
}
.container {
  background-color: white;
  padding : 20px;
  width: 100%;
  max-width: 600px;
  position:relative;
  box-shadow: 0 2px 4px #888888;
}

h2 {
  font-size: 24px;
  color: #000000;
  margin-bottom: 5px;
  margin-top: 5px;
  font-weight: bold;
  padding-top: 5px;
  text-shadow: 0 2px 4px #cdcdcd;
}

.counter-section {
  margin-bottom: 10px;
}

.counter-display {
  font-size: 20px;
  font-weight: bold;
  color: #3C79F5;
}

.color-changer-section {
  border-bottom: 2px solid #ccc;
  border-top: 2px solid #ccc;
  padding: 20px; 
}

.color-box {
  width: 100px;
  height: 100px;
  background-color: #3498db;
  margin: 20px auto;
  border-radius: 50px;
  box-shadow: 0 2px 4px #888888;
}

.btn {
  background-color: #6C00FF;
  color: white;
  border: none;
  padding: 10px 20px;
  margin: 10px;
  font-size: 1em;
  cursor: pointer;
  border-radius: 20px;
  transition: background-color 0.3s ease;
  box-shadow: 0 2px 4px #888888;
}

.btn:hover {
  background-color: #5a03d4;
  box-shadow: 0 4px 6px #535353;
}

.carousel {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

.carousel img {
  max-width: 400px;
  max-height: 300px;
  border-radius: 5px;
  transition: transform 0.5s ease;
  box-shadow: 0 2px 4px #535353;
}

/* .fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
} */

/* .fade-enter, .fade-leave-to {
  opacity: 0;
} */
</style>

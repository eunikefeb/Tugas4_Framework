<template>
  <div id="app" class="app-container">
    <h1>Vue Eunike Febianti</h1>

    <!-- Click Counter -->
    <div class="counter-section">
      <button @click="incrementCounter">Clicked {{ counter }} times</button>
    </div>

    <!-- Box Color Changer -->
    <div class="color-changer-section">
      <div class="color-box" :style="{ backgroundColor: currentColor }"></div>
      <button @click="changeColor">Change Color</button>
    </div>

    <!-- Image Carousel -->
    <div class="carousel-section">
      <div class="carousel">
        <img :src="images[currentImageIndex]" alt="carousel image" class="carousel-image" />
        <div class="carousel-buttons">
          <button @click="prevImage">Previous</button>
          <button @click="nextImage">Next</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// Import foto dari assets
import photo1 from '@/assets/niek1.jpg';
import photo2 from '@/assets/niek2.jpg';
import photo3 from '@/assets/niek3.jpg';

export default {
  data() {
    return {
      // Counter state
      counter: 0,

      // Color Changer state
      colors: ["red", "blue", "green", "yellow", "purple"],
      currentColorIndex: 0,

      // Image Carousel state
      images: [photo1, photo2, photo3], // gunakan foto yang diimpor
      currentImageIndex: 0,
    };
  },
  methods: {
    // Counter function
    incrementCounter() {
      this.counter++;
    },

    // Color Changer function
    changeColor() {
      this.currentColorIndex = (this.currentColorIndex + 1) % this.colors.length;
    },

    // Carousel functions
    prevImage() {
      this.currentImageIndex =
        (this.currentImageIndex - 1 + this.images.length) % this.images.length;
    },
    nextImage() {
      this.currentImageIndex = (this.currentImageIndex + 1) % this.images.length;
    },
  },
  computed: {
    // Get current color
    currentColor() {
      return this.colors[this.currentColorIndex];
    },
  },
};
</script>

<style scoped>
.app-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  padding: 20px;
  text-align: center;
}

h1 {
  margin-bottom: 20px;
  font-size: 1.5rem;
  color: #333;
}

.counter-section,
.color-changer-section,
.carousel-section {
  margin: 20px 0;
  width: 100%;
  max-width: 400px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.color-box {
  width: 100px;
  height: 100px;
  margin: 10px 0;
  border: 1px solid #ccc;
  transition: background-color 0.3s;
}

.carousel {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.carousel-image {
  width: 300px;
  height: 200px;
  object-fit: cover;
  margin-bottom: 10px;
  border-radius: 8px;
  border: 2px solid #ddd;
}

.carousel-buttons {
  display: flex;
  gap: 10px;
}

button {
  padding: 10px 20px;
  border: none;
  background-color: #007bff;
  color: #fff;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #0056b3;
}
</style>

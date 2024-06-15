<template>
  <div class="header-container"> 
    <section class="header-content">
      <img src="../assets/logo2.svg" alt="Summit Paint and Construction" class="fadeIn hero-img" />
      <h1 class="title fadeInUp">
        <span class="highlight">Peak Quality</span> at a Fair Price
      </h1>
      <p class="intro-text fadeInUp">Summit is a residential and commercial painting company in City, State</p>
      <div class="actions">
        <a class="btn-primary fadeInScale" @click.prevent="navigateToSection('contactSection')">
          Let’s Talk
        </a>
        <a class="btn-secondary fadeInScale" @click.prevent="navigateToSection('gallerySection')">
          View Our Work
        </a>
      </div>

    </section>
  </div>
</template>

<script>
import image1 from '../assets/images/carousel_1.png';
import image2 from '../assets/images/carousel_2.png';
import image3 from '../assets/images/carousel_3.png';
import image4 from '../assets/images/carousel_4.png';

export default {
  name: 'HeaderComponent',
  data() {
    return {
      images: [image1, image2, image3, image4],
      currentSlide: 0
    };
  },
  methods: {
    navigateToSection(sectionId) {
      this.$emit('navigateToSection', sectionId);
      if (this.isMobile) {
        this.isOpen = false;
      }
    },
    nextSlide() {
      this.currentSlide = (this.currentSlide + 1) % this.images.length;
    },
    prevSlide() {
      this.currentSlide = (this.currentSlide + this.images.length - 1) % this.images.length;
    },
    goToSlide(index) {
      this.currentSlide = index;
    }
  }
};
</script>


<style scoped>

@font-face {
  font-family: 'K2D';
  src: url('../assets/fonts/K2D-Regular.ttf') format('truetype');
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: 'K2D';
  src: url('../assets/fonts/K2D-Bold.ttf') format('truetype');
  font-weight: bold;
  font-style: normal;
}

@font-face {
  font-family: 'K2D';
  src: url('../assets/fonts/K2D-Medium.ttf') format('truetype');
  font-weight: 600;
  font-style: normal;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

.fadeIn {
  animation: fadeIn 2s ease-in-out;
}

@keyframes fadeInUp {
  0% {
    opacity: 0;
    transform: translateY(20px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

.fadeInUp {
  animation: fadeInUp 1.5s ease-out;
}

@keyframes fadeInScale {
  0% {
    opacity: 0;
    transform: scale(0.8);
  }
  100% {
    opacity: 1;
    transform: scale(1);
  }
}

.fadeInScale {
  animation: fadeInScale 1.5s ease-in-out;
}

.header-container {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: url('../assets/images/carousel_1.png') center center/cover no-repeat;
  position: relative; /* Ensure positioning context for z-index */
  z-index: 0; /* Adjust this as necessary */
}

.header-container::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.75);
  z-index: -1; /* Ensure it is behind the content */
}

.header-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 48px;
  width: 60%;
  position: relative; /* Ensure it is above the background */
  z-index: 1; /* Ensure it is above the ::before pseudo-element */
}

.actions {
  display: flex;
  flex-wrap: wrap;
  gap: 32px;
  position: relative; /* Ensure it inherits the z-index context */
  z-index: 1; /* Make sure it's above any other overlapping elements */
}

.btn-secondary, .btn-primary {
  position: relative; /* Ensure they are positioned within the z-index context */
  z-index: 1; /* Ensure they are above the background overlay */
}

.hero-img {
  width: 25%;
  height: auto;
}

h1 {
  font-size: 3rem;
  font-family: 'K2D', sans-serif;
  font-weight: bold;
  color: #fff;
}

p{
  color: #fff;
}

@media (max-width: 768px) {
  .header-container {
    flex-direction: column;
    padding: 32px;
    box-sizing: border-box;
  }

  .header-carousel, .header-content {
    width: 100%;
  }

  .header-content .title {
    font-size: 1.5rem;
  }

  .header-content .intro-text {
    font-size: 1rem;
  }

  .actions a{
    width: 100%;
  }
}
</style>
<template>
  <div class="header-container">
    <section class="header-carousel">
      <div class="carousel-wrapper">
        <button class="carousel-arrow left" @click="prevSlide">&#9664;</button>
        <div class="carousel">
          <div 
            v-for="(image, index) in images" 
            :key="index" 
            :class="['carousel-slide', { active: index === currentSlide }]"
          >
            <img :src="image" :alt="'Slide ' + (index + 1)" />
          </div>
        </div>
        <button class="carousel-arrow right" @click="nextSlide">&#9654;</button>
      </div>
      <div class="carousel-indicators">
        <div 
          v-for="(image, index) in images" 
          :key="index" 
          :class="['indicator', { active: index === currentSlide }]"
          @click="goToSlide(index)"
        >
          <div class="inner-circle"></div>
        </div>
      </div>
    </section>
    <section class="header-content">
      <h1 class="title fadeInUp">
        Summit<br />Paint and Construction
      </h1>
      <p class="intro-text fadeInUp">Residential and Commercial Painting company in City, State</p>
      <a class="btn-primary fadeInScale" @click.prevent="navigateToSection('contactSection')">
        Let’s Talk
      </a>
    </section>
  </div>
</template>

<script>
export default {
  name: 'HeaderComponent',
  data() {
    return {
      images: [
        '../assets/images/carousel_1.png',
        '../assets/images/carousel_1.png',
        '../assets/images/carousel_1.png',
        '../assets/images/carousel_1.png'
      ],
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
    },
  }
};
</script>

<style scoped>
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
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  padding: 64px;
  box-sizing: border-box;
}

.header-carousel, .header-content {
  width: 45%;
}

.header-content{
  display: flex;
  flex-direction: column;
  gap: 32px;
}

.carousel-wrapper {
  display: flex;
  align-items: center;
}

.carousel {
  display: flex;
  overflow: hidden;
  width: 100%;
  justify-content: center;
}

.carousel-slide {
  min-width: 100%;
  transition: transform 0.5s ease;
}

.carousel-slide.active {
  transform: translateX(-100%);
}

.carousel-arrow {
  background-color: #4475F4;
  color: white;
  border: none;
  cursor: pointer;
  padding: 10px;
}

.carousel-indicators {
  display: flex;
  justify-content: center;
  margin-top: 10px;
}

.indicator {
  width: 16px;
  height: 16px;
  border: 1px solid #9c9c9c;
  border-radius: 50%;
  margin: 0 5px;
  position: relative;
  cursor: pointer;
}

.indicator.active {
  border-color: #4475F4;
}

.indicator.active .inner-circle {
  width: 10px;
  height: 10px;
  background-color: #4475F4;
  border-radius: 50%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

@media (max-width: 768px) {
  .header-container {
    flex-direction: column;
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
}
</style>

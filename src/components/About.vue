<template>
  <section class="team-section fadeIn" ref="aboutSection">
    <div class="about-words">
      <div class="section-header">
      <div class="section-header-small">
      <h5>Team</h5>
      <div class="header-line"></div>
      </div>
      <h2>Meet the <span class="highlight">Team</span></h2>
      </div>
      <p>Our team of experts is here to help you with all your painting needs. We are dedicated to providing the best service and quality workmanship. We provide a plethora of services:</p>
      <div class="services">
          <div class="service"><img src="../assets/icons/interior.svg" alt="Interior"/><p>Interior Painting</p></div>
          <div class="service"><img src="../assets/icons/deck.svg" alt="Exterior" /><p>Exterior Painting</p></div>
          <div class="service"><img src="../assets/icons/business.svg" alt="Commercial" /><p>Commercial Painting</p></div>
          <div class="service"><img src="../assets/icons/home.svg" alt="Residential" /><p>Residential Painting</p></div>
          <div class="service"><img src="../assets/icons/color.svg" alt="Color" /><p>Color Consultation</p></div>
          <div class="service"><img src="../assets/icons/water.svg" alt="Color" /><p>Power Washing</p></div>
        </div>
    </div>
    <div class="about-carousel">
      <div class="carousel-wrapper">
        <div class="carousel">
          <div v-for="(image, index) in images" :key="index" :class="['carousel-slide', { active: index === currentSlide }]">
            <img :src="image" :alt="'Slide ' + (index + 1)" class="carousel-image" />
          </div>
        </div>
      </div>
      <div class="carousel-indicators">
        <button class="carousel-indicator-arrow left" @click="prevSlide">&#9664;</button>
        <div v-for="(image, index) in images" :key="index" :class="['indicator', { active: index === currentSlide }]" @click="goToSlide(index)">
          <div class="inner-circle"></div>
        </div>
        <button class="carousel-indicator-arrow right" @click="nextSlide">&#9654;</button>
      </div>
    </div>
  </section>
</template>

<script>

import image1 from '../assets/images/carousel_1.png';
import image2 from '../assets/images/carousel_2.png';
import image3 from '../assets/images/carousel_3.png';
import image4 from '../assets/images/carousel_4.png';

export default {
  name: 'AboutComponent',
  data() {
    return {
      images: [image1, image2, image3, image4],
      currentSlide: 0
    };
  },
  mounted() {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          this.$refs.aboutSection.classList.add('fadeIn-visible');
          observer.unobserve(this.$refs.aboutSection);
        }
      });
    }, {
      threshold: 0.1
    });

    observer.observe(this.$refs.aboutSection);
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

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

.fadeIn {
  opacity: 0; /* Initial hidden state */
  transition: opacity 1s ease-in-out;
}

.fadeIn.fadeIn-visible {
  opacity: 1; /* Visible state */
}

.team-section{
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 32px;
  padding: 120px 64px;
  background-color: #f5f9ff;
}

.about-words {
  display: flex;
  flex-direction: column;
  gap: 40px;
}

.services{
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
}

.service{
  display: flex;
  gap: 16px;
  align-items: center;
  width: 45%;
}

.service p{
  font-size: 16px;
  font-weight: 500;
}

.about-carousel, .about-words {
  width: 45%;
}

.carousel-wrapper {
  display: flex;
  align-items: center;
  position: relative;
  width: 100%;
}

.carousel {
  display: flex;
  width: 100%;
  height: 100%;
}

.carousel-slide {
  min-width: 100%;
  transition: opacity 0.5s ease;
  opacity: 0;
  display: none;
  height: 100%;
}

.carousel-slide.active {
  opacity: 1;
  display: block;
}

.carousel-image {
  width: 100%;
  height: 368px;
  border-radius: 16px;
  object-fit: cover;
}

.carousel-arrow {
  color: #4475F4;
  border: none;
  cursor: pointer;
  padding: 16px;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  z-index: 1;
}

.carousel-arrow.left {
  left: 0;
}

.carousel-arrow.right {
  right: 0;
}

.carousel-indicators {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 32px;
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

.carousel-indicator-arrow {
  color: #4475F4;
  background-color: transparent;
  border: none;
  cursor: pointer;
  padding: 8px;
  margin: 0 10px;
}

@media (max-width: 900px) {
  .team-section {
    justify-content: center;
  }

  .about-carousel, .about-words {
    width: 80%;
  }
}

@media (max-width:600px) {
  .team-section {
    padding: 32px;
  }

  .service p{
    font-size: 14px;
  }

  .about-carousel, .about-words {
    width: 100%;
  }
}

</style>
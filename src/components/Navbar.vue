<template>
  <nav class="navbar" ref="navbarSection">
    <a href="#" @click.prevent="navigateToSection('navbarSection')">
      <div class="nav-logo">
        <img src="../assets/logo.svg" alt="ClearStack AI" class="logo" />
      </div>
    </a>
    <div class="nav-links-wrapper">
      <div class="nav-links" :class="{ 'nav-links-mobile': isMobile, 'nav-links-open': isMobile && isOpen }">
        <a href="#" @click.prevent="navigateToSection('aboutSection')">About Us</a>
        <a href="#" @click.prevent="navigateToSection('gallerySection')">Gallery</a>
        <a href="#" @click.prevent="navigateToSection('contactSection')">Contact</a>
        <!-- Only include the button in the mobile nav links -->
        <a v-if="isMobile" class="btn-primary mobile-btn" @click.prevent="navigateToSection('contactSection')">Contact Us</a>
      </div>
    </div>
    <!-- Exclude the button from desktop nav links -->
    <a v-if="!isMobile" class="btn-primary" @click.prevent="navigateToSection('contactSection')">Contact Us</a>
    <div class="hamburger" @click="toggleMenu">
      <div class="line" :class="{ 'line1': isOpen }"></div>
      <div class="line" :class="{ 'line2': isOpen }"></div>
      <div class="line" :class="{ 'line3': isOpen }"></div>
    </div>
  </nav>
</template>



<script>
export default {
  name: 'NavbarComponent',
  data() {
    return {
      isOpen: false,
      isMobile: window.innerWidth <= 768
    };
  },
  methods: {
    toggleMenu() {
      this.isOpen = !this.isOpen;
    },
    updateIsMobile() {
      this.isMobile = window.innerWidth <= 768;
      if (!this.isMobile) {
        this.isOpen = false;
      }
    },
    navigateToSection(sectionId) {
      this.$emit('navigateToSection', sectionId);
      if (this.isMobile) {
        this.isOpen = false;
      }
    }
  },
  mounted() {
    window.addEventListener('resize', this.updateIsMobile);
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.updateIsMobile);
  }
};
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 60px;
  background-color: rgba(0, 0, 0, 0.9);
  width: 100%;
  box-sizing: border-box;
  height: 100px;
}

.nav-logo {
  display: flex;
  align-items: center;
}

.nav-links-wrapper {
  flex-grow: 1;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-left: 64px;
}

.nav-links {
  display: flex;
  gap: 64px;
  align-items: end;
}

.nav-links a {
  color: #fff;
  font-weight: normal;
  font-size: 16px;
  text-decoration: none;
}

.nav-links a:hover {
  color: #0C3EC0;
  font-weight: 600;
  text-decoration: none;
}

.nav-links-mobile {
  display: none;
  box-sizing: border-box;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  background-color: white;
  position: absolute;
  top: 100px;
  left: 0;
  width: 100%;
  padding: 20px;
  z-index: 10;
  border-radius: 0px;
  border-top: 1px solid #4173F3;
  background-color: rgba(0, 0, 0, 0.9);
  box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.25);
}

.nav-links-mobile > a {
  padding: 12px;
  border-bottom: 1px solid #4173F3;
  width: 100%;
  text-align: center;
}

.nav-links-mobile > .mobile-btn {
  align-self: center;
}

.nav-links-open {
  display: flex !important;
}

.mobile-btn {
  width: 100%;
}

.logo {
  height: 32px;
}

.hamburger {
  display: none;
  flex-direction: column;
  cursor: pointer;
  gap: 5px;
}

.hamburger .line {
  width: 28px;
  height: 3px;
  background-color: #4173F3;
  transition: 0.3s;
}

.hamburger .line1 {
  transform: rotate(45deg) translate(5.5px, 5.5px);
}

.hamburger .line2 {
  opacity: 0;
}

.hamburger .line3 {
  transform: rotate(-45deg) translate(5.5px, -5.5px);
}

@media (max-width: 768px) {
  .logo {
    height: 48px;
  }

  .nav-links-wrapper {
    margin-left: 0;
  }

  .nav-links {
    display: none;
  }

  .hamburger {
    display: flex;
  }
}
</style>
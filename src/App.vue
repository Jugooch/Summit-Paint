<template>
  <div class="main-wrapper">
    <header class="header-container">
      <section ref="navbarSection">
        <NavbarComponent @navigateToSection="scrollToSection" />
      </section>
      <HeaderComponent @navigateToSection="scrollToSection" />
    </header>
    
    <main>
      <section ref="aboutSection">
        <AboutComponent />
      </section>
      <section ref="gallerySection">
        <GalleryComponent />
      </section>
      <section ref="contactSection">
        <ContactComponent />
      </section>
    </main>
    <FooterComponent @navigateToSection="scrollToSection" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import NavbarComponent from './components/Navbar.vue';
import HeaderComponent from './components/Hero.vue';
import AboutComponent from './components/About.vue';
import GalleryComponent from './components/Gallery.vue';
import ContactComponent from './components/Contact.vue';
import FooterComponent from './components/Footer.vue';

export default defineComponent({
  name: 'App',
  components: {
    HeaderComponent,
    AboutComponent,
    GalleryComponent,
    ContactComponent,
    FooterComponent,
    NavbarComponent
  },
  methods: {
    scrollToSection(sectionId) {
      const section = this.$refs[sectionId];
      if (section) {
        section.scrollIntoView({ behavior: 'smooth' });
      }
    }
  }
});
</script>


<style>
body,
html {
  margin: 0px;
  padding: 0px;
  overflow-x: hidden;
  height: 100%;
  width: 100%;
  font-family: "Inter", sans-serif;
}

.main-wrapper {
  display: flex;
  flex-direction: column;
}

main {
  display: flex;
  flex-direction: column;
}

.header-container {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100vh;
}

.btn-primary {
  color: white;
  background-color: #4173F3;
  font-size: 16px;
  font-weight: 500;
  border-radius: 8px;
  padding: 12px 32px;
  border: none;
  cursor: pointer;
  width: fit-content;
  width: -moz-fit-content;
}

.btn-primary:hover {
  background-color: #003B80;
}

.btn-secondary {
  color: #fff;
  background-color: transparent;
  font-size: 16px;
  font-weight: 500;
  border-radius: 8px;
  padding: 12px 32px;
  border: 1px solid white;
  cursor: pointer;
  width: fit-content;
  width: -moz-fit-content;
}

.btn-secondary:hover {
  border-color: #4173F3;
  color: #4173F3;
}

.btn-tertiary {
  color: #4173F3;
  background-color: #F5F8FE;
  font-size: 16px;
  font-weight: 500;
  border-radius: 8px;
  padding: 12px 32px;
  border: 1px solid #4173F3;
  cursor: pointer;
  width: fit-content;
  width: -moz-fit-content;
}

.btn-tertiary:hover {
  background-color: #CFDCFC;
}

h1 {
  color: #4173F3;
  font-size: 40px;
  font-weight: 700;
  margin: 0px;
  padding: 0px;
}

h2 {
  color: #010818;
  font-size: 32px;
  font-weight: 700;
  margin: 0px;
  padding: 0px;
}

h3 {
  color: #010818;
  font-size: 48px;
  font-weight: 300;
  margin: 0px;
  padding: 0px;
}

h4 {
  color: #010818;
  font-size: 16px;
  font-weight: 700;
  margin: 0px;
  padding: 0px;
}

h5 {
  color: #8f8f8f;
  font-size: 16px;
  font-weight:lighter;
  margin: 0px;
  padding: 0px;
}

p {
  color: #010818;
  font-size: 20px;
  font-weight: normal;
  margin: 0px;
  padding: 0px;
}

a {
  text-decoration: none;
}

.highlight {
  color: #4173F3;
}

.section-header {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  width: fit-content;
}

.section-header-small {
  display: flex;
  align-items: center;
  margin-bottom: 4px; /* Gap between small header and h2 */
}

.section-header-small .header-line {
  flex-grow: 1; /* Allows the line to grow and fill the space */
  height: 1px; /* Adjust the height of the line */
  background-color: #4173F3; /* Adjust color as needed */
  margin-left: 8px; /* Gap between h5 and line */
}

.section-header-small {
  width: 100%;
}

.section-header-small .header-line {
  margin-left: 8px; /* Gap between h5 and line */
}


@media (max-width: 600px) {
  h1 {
    font-size: 32px;
  }

  h2 {
    font-size: 24px;
  }

  h3 {
    font-size: 32px;
  }

  p {
    font-size: 16px;
  }
}
</style>

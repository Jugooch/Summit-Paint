<template>
  <div class="main-wrapper">
    <header class="header-container">
      <section ref="navbarSection">
        <NavbarComponent @navigateToSection="scrollToSection" />
      </section>
      <HeaderComponent @navigateToSection="scrollToSection" />
    </header>
    
    <main>
      <section ref="servicesSection">
        <ServicesComponent  @navigateToSection="scrollToSection" />
      </section>
      <section ref="teamSection">
        <TeamComponent />
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
import HeaderComponent from './components/Hero.vue';
import TeamComponent from './components/Team.vue';
import ContactComponent from './components/Contact.vue';
import FooterComponent from './components/Footer.vue';
import NavbarComponent from './components/Navbar.vue';

export default defineComponent({
  name: 'App',
  components: {
    HeaderComponent,
    TeamComponent,
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
  border-radius: 66px;
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
  color: #4173F3;
  background-color: #F5F8FE;
  font-size: 16px;
  font-weight: 500;
  border-radius: 66px;
  padding: 12px 32px;
  border: none;
  cursor: pointer;
  width: fit-content;
  width: -moz-fit-content;
}

.btn-secondary:hover {
  background-color: #CFDCFC;
}

.btn-tertiary {
  color: #4173F3;
  background-color: #F5F8FE;
  font-size: 16px;
  font-weight: 500;
  border-radius: 66px;
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
  font-size: 64px;
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
  text-align: center;
  font-size: 24px;
  font-weight: 700;
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

  h4 {
    font-size: 24px;
  }

  p {
    font-size: 16px;
  }
}
</style>

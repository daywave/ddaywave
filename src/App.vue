<template>
  <div id="app">
    <MouseTracker />
    <navbar-section />
    <section id="header">
      <header-section />
    </section>
    <section id="about">
      <about-section />
    </section>
    <section id="cv">
      <cv-section />
    </section>
    <section id="education">
      <education-section />
    </section>
    <section id="courses">
      <courses-section />
    </section>
    <footer id="footer">
      <footer-section />
    </footer>
  </div>
</template>

<script>
//importacion de componentes
import HeaderSection from './components/HeaderSection.vue';
import NavbarSection from './components/NavbarSection.vue';
import AboutSection from './components/AboutSection.vue';
import CvSection from './components/CvSection.vue';
import CoursesSection from './components/CoursesSection.vue';
import FooterSection from './components/FooterSection.vue';
import EducationSection from './components/EducationSection.vue';
import MouseTracker from "@/components/Animations/MouseTracker.vue";

export default {
  name: 'App',
  components: {
    NavbarSection,
    HeaderSection,
    AboutSection,
    CvSection,
    CoursesSection,
    FooterSection,
    EducationSection,
    MouseTracker
  }
}
</script>

<style>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  box-sizing: border-box;
}

</style>

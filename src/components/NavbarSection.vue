<template>
  <nav :class="['navbar', { 'scrolled': isScrolled }]">
    <div class="navbar-brand">
      <h1>ddaywave.</h1>
    </div>
    <div class="navbar-buttons">
      <button @click="scrollToSection('header')"><span class="nav-number">01</span> <span class="nav-text">// Home</span></button>
      <button @click="scrollToSection('about')"><span class="nav-number">02</span> <span class="nav-text">// About me</span></button>
      <button @click="scrollToSection('cv')"><span class="nav-number">03</span> <span class="nav-text">// Skills</span></button>
      <button @click="scrollToSection('education')"><span class="nav-number">04</span> <span class="nav-text">// Education</span></button>
      <button @click="scrollToSection('courses')"><span class="nav-number">05</span> <span class="nav-text">// Courses</span></button>
      <button @click="scrollToSection('footer')"><span class="nav-number">06</span> <span class="nav-text">// Contact</span></button>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'NavbarSection',
  data() {
    return {
      isScrolled: false
    };
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      this.isScrolled = window.scrollY > 50;
    },
    scrollToSection(sectionId) {
      const section = document.getElementById(sectionId);
      if (section) {
        const yOffset = -70; // Ajusta según la altura de tu navbar
        const y = section.getBoundingClientRect().top + window.pageYOffset + yOffset;
        window.scrollTo({ top: y, behavior: 'smooth' });
      }
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;700&display=swap');

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
  position: fixed;
  width: 100%;
  transition: background-color 0.3s, box-shadow 0.3s, border-bottom 0.3s;
  color: white;
  z-index: 10;
  background-color: transparent; /* Transparent initially */
  font-family: 'Fira Code', monospace;
}
.navbar.scrolled {
  background-color: #000000;
  box-shadow: 0 4px 2px -2px rgba(0, 0, 0, 0.7);
  border-bottom: 2px solid #6DA5C0; /* Border bottom when scrolled */
}
.navbar-brand h1 {
  font-size: 2rem;
  margin: 0;
  color: #f39c12;
  text-shadow: 0 0 10px rgba(255, 165, 0, 0.7);
}
.navbar-buttons {
  display: flex;
  align-items: center;
}
.navbar-buttons button {
  margin-left: 1rem;
  background: none;
  border: none;
  color: #c5c6c7;
  cursor: pointer;
  font-size: 1rem;
  transition: color 0.3s, border-bottom 0.3s;
  font-family: 'Fira Code', monospace;
  position: relative;
  display: flex;
  align-items: center;
}
.navbar-buttons button .nav-number {
  font-size: 0.8rem;
  margin-right: 0.5rem;
  color: #6DA5C0; /* Color del número */
}
.navbar-buttons button .nav-text {
  font-size: 1rem;
  color: white; /* Color del texto */
}
.navbar-buttons button::before {
  content: '|';
  margin-right: 1rem;
  color: #6DA5C0; /* Color de la línea separadora */
}
.navbar-buttons button:first-child::before {
  content: ''; /* Eliminar la línea separadora del primer botón */
}
.navbar-buttons button:hover .nav-text {
  color: #f39c12;
}
.navbar-buttons button:hover::before {
  color: #f39c12; /* Cambiar el color de la línea separadora al hacer hover */
}
</style>

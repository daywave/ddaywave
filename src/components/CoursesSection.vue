<template>
  <section class="courses-section">
    <div class="content">
      <h2 class="glitch" data-text="Personal Courses">Personal Courses</h2>
      <div class="courses-container">
        <div v-for="(course, index) in courses" :key="index" class="course-icon-card" @click="toggleCard(index)">
          <div class="icon-and-title">
            <i :class="course.icon" class="course-icon"></i>
            <h3>{{ course.title }}</h3>
            <i class="fas fa-chevron-down toggle-icon"></i>
          </div>
          <transition name="fade">
            <div v-if="activeIndex === index" class="course-card">
              <p>{{ course.text }}</p>
              <span class="course-platform">{{ course.platform }}</span>
            </div>
          </transition>
        </div>
      </div>
      <div class="lottie-container">
        <AnimationDev :animationData="DevAnimationData" />
      </div>
    </div>
  </section>
</template>

<script>
import AnimationDev from '@/components/Animations/AnimationDev.vue';
import DevAnimationData from '@/assets/AnimationDev.json';

export default {
  name: 'CoursesSection',
  components: {
    AnimationDev
  },
  data() {
    return {
      DevAnimationData,
      activeIndex: null,
      courses: [
        { title: 'Vue3: Composition and VUEX', text: 'Detailed course on Vue3 Composition and VUEX', platform: 'Udemy', icon: 'fab fa-vuejs' },
        { title: 'VUE3 + NETCORE + EFC', text: 'Comprehensive guide on VUE3 with NETCORE and EFC', platform: 'Udemy', icon: 'fab fa-vuejs' },
        { title: 'Wireshark Crash Course', text: 'Quick and effective course on Wireshark', platform: 'Udemy', icon: 'fas fa-network-wired' },
        { title: 'Ethically Hack', text: 'Learn ethical hacking principles', platform: 'Udemy', icon: 'fas fa-user-secret' },
        { title: 'Ethical Hacking: Linux Privilege Escalation', text: 'Advanced course on privilege escalation in Linux', platform: 'Udemy', icon: 'fab fa-linux' },
        { title: 'Bilingual Team Working', text: 'Enhance your teamwork skills with a bilingual approach', platform: 'PROAKATEMIA', icon: 'fas fa-users' },
      ]
    };
  },
  methods: {
    toggleCard(index) {
      this.activeIndex = this.activeIndex === index ? null : index;
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;700&display=swap');

.courses-section {
  background-color: #000000; /* Fondo negro */
  color: #c5c8c6; /* Texto gris claro */
  padding: 4rem 2rem;
  text-align: center;
  font-family: 'Fira Code', monospace;
  overflow: hidden;
  position: relative;
}

.content {
  max-width: 1200px; /* Aumenta el ancho máximo */
  margin: 0 auto;
  position: relative;
  z-index: 2;
}

.courses-section h2 {
  font-size: 2.5rem;
  margin-bottom: 2rem;
  position: relative;
  color: #6DA5C0; /* Color neón */
  text-shadow: 0 0 5px #6DA5C0, 0 0 10px #6DA5C0, 0 0 20px #6DA5C0, 0 0 40px #6DA5C0, 0 0 80px #6DA5C0;
}

.courses-section h2::after {
  content: '';
  width: 50px;
  height: 4px;
  background-color: #6DA5C0; /* Color del subrayado */
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  box-shadow: 0 0 5px #6DA5C0, 0 0 10px #6DA5C0, 0 0 20px #6DA5C0, 0 0 40px #6DA5C0, 0 0 80px #6DA5C0;
}

.courses-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.course-icon-card {
  background-color: #1b1e34; /* Color de fondo */
  border-radius: 8px;
  padding: 1rem;
  margin: 1rem;
  width: 30%;
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.course-icon-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.icon-and-title {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.course-icon {
  font-size: 2rem;
  margin-right: 1rem;
  color: #6DA5C0;
}

.toggle-icon {
  font-size: 1.5rem;
  color: #6DA5C0;
}

.course-card {
  margin-top: 1rem;
  background-color: #101223;
  padding: 1rem;
  border-radius: 8px;
}

.course-card p,
.course-card .course-platform {
  margin: 0.5rem 0;
}

.course-platform {
  font-size: 0.875rem;
  color: #9aaab4; /* Color secundario para la plataforma */
}

.lottie-container {
  margin-top: 2rem;
  width: 100%;
  display: flex;
  justify-content: center;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}

/* Glitch Effect */
.glitch {
  position: relative;
  color: #c5c8c6;
  display: inline-block;
}

.glitch::before,
.glitch::after {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: inherit;
}

.glitch::before {
  left: 2px;
  text-shadow: -2px 0 #ff00c1;
  clip: rect(24px, 550px, 90px, 0);
  animation: glitch-anim 2s infinite linear alternate-reverse;
}

.glitch::after {
  left: -2px;
  text-shadow: -2px 0 #00fff9, 2px 2px #ff00c1;
  clip: rect(85px, 550px, 140px, 0);
  animation: glitch-anim2 3s infinite linear alternate-reverse;
}

@keyframes glitch-anim {
  0% {
    clip: rect(42px, 550px, 44px, 0);
    transform: skew(0.3deg);
  }
  5% {
    clip: rect(12px, 550px, 60px, 0);
    transform: skew(0.3deg);
  }
  10% {
    clip: rect(62px, 550px, 84px, 0);
    transform: skew(0.3deg);
  }
  15% {
    clip: rect(42px, 550px, 22px, 0);
    transform: skew(0.3deg);
  }
  20% {
    clip: rect(12px, 550px, 90px, 0);
    transform: skew(0.3deg);
  }
  25% {
    clip: rect(42px, 550px, 72px, 0);
    transform: skew(0.3deg);
  }
  30% {
    clip: rect(92px, 550px, 88px, 0);
    transform: skew(0.3deg);
  }
  35% {
    clip: rect(22px, 550px, 78px, 0);
    transform: skew(0.3deg);
  }
  40% {
    clip: rect(42px, 550px, 74px, 0);
    transform: skew(0.3deg);
  }
  45% {
    clip: rect(12px, 550px, 50px, 0);
    transform: skew(0.3deg);
  }
  50% {
    clip: rect(62px, 550px, 60px, 0);
    transform: skew(0.3deg);
  }
  55% {
    clip: rect(72px, 550px, 82px, 0);
    transform: skew(0.3deg);
  }
  60% {
    clip: rect(52px, 550px, 92px, 0);
    transform: skew(0.3deg);
  }
  65% {
    clip: rect(22px, 550px, 44px, 0);
    transform: skew(0.3deg);
  }
  70% {
    clip: rect(92px, 550px, 22px, 0);
    transform: skew(0.3deg);
  }
  75% {
    clip: rect(52px, 550px, 74px, 0);
    transform: skew(0.3deg);
  }
  80% {
    clip: rect(12px, 550px, 90px, 0);
    transform: skew(0.3deg);
  }
  85% {
    clip: rect(42px, 550px, 72px, 0);
    transform: skew(0.3deg);
  }
  90% {
    clip: rect(92px, 550px, 88px, 0);
    transform: skew(0.3deg);
  }
  95% {
    clip: rect(22px, 550px, 78px, 0);
    transform: skew(0.3deg);
  }
  100% {
    clip: rect(42px, 550px, 74px, 0);
    transform: skew(0.3deg);
  }
}

@keyframes glitch-anim2 {
  0% {
    clip: rect(52px, 550px, 50px, 0);
    transform: skew(0.3deg);
  }
  5% {
    clip: rect(22px, 550px, 70px, 0);
    transform: skew(0.3deg);
  }
  10% {
    clip: rect(82px, 550px, 44px, 0);
    transform: skew(0.3deg);
  }
  15% {
    clip: rect(52px, 550px, 42px, 0);
    transform: skew(0.3deg);
  }
  20% {
    clip: rect(22px, 550px, 50px, 0);
    transform: skew(0.3deg);
  }
  25% {
    clip: rect(52px, 550px, 62px, 0);
    transform: skew(0.3deg);
  }
  30% {
    clip: rect(82px, 550px, 78px, 0);
    transform: skew(0.3deg);
  }
  35% {
    clip: rect(62px, 550px, 68px, 0);
    transform: skew(0.3deg);
  }
  40% {
    clip: rect(52px, 550px, 54px, 0);
    transform: skew(0.3deg);
  }
  45% {
    clip: rect(42px, 550px, 80px, 0);
    transform: skew(0.3deg);
  }
  50% {
    clip: rect(72px, 550px, 62px, 0);
    transform: skew(0.3deg);
  }
  55% {
    clip: rect(52px, 550px, 82px, 0);
    transform: skew(0.3deg);
  }
  60% {
    clip: rect(32px, 550px, 62px, 0);
    transform: skew(0.3deg);
  }
  65% {
    clip: rect(62px, 550px, 42px, 0);
    transform: skew(0.3deg);
  }
  70% {
    clip: rect(82px, 550px, 50px, 0);
    transform: skew(0.3deg);
  }
  75% {
    clip: rect(72px, 550px, 84px, 0);
    transform: skew(0.3deg);
  }
  80% {
    clip: rect(52px, 550px, 60px, 0);
    transform: skew(0.3deg);
  }
  85% {
    clip: rect(62px, 550px, 44px, 0);
    transform: skew(0.3deg);
  }
  90% {
    clip: rect(82px, 550px, 78px, 0);
    transform: skew(0.3deg);
  }
  95% {
    clip: rect(72px, 550px, 88px, 0);
    transform: skew(0.3deg);
  }
  100% {
    clip: rect(62px, 550px, 74px, 0);
    transform: skew(0.3deg);
  }
}

@media (max-width: 1024px) {
  .course-icon-card {
    width: 45%; /* Ajustar el ancho para pantallas medianas */
  }

  .courses-container {
    justify-content: center; /* Centrar los elementos */
  }

  .course-icon {
    font-size: 1.5rem; /* Ajustar tamaño del icono para pantallas medianas */
  }

  .toggle-icon {
    font-size: 1.25rem; /* Ajustar tamaño del icono para pantallas medianas */
  }
}

@media (max-width: 768px) {
  .content {
    flex-direction: column;
    align-items: center;
  }
  .courses-container {
    flex-direction: column; /* Organizar en una columna para pantallas pequeñas */
    align-items: center;
  }
  .course-icon-card {
    width: 90%; /* Ajustar el ancho para pantallas pequeñas */
    margin: 1rem 0; /* Agregar margen vertical */
  }
  .course-icon {
    font-size: 1.5rem; /* Ajustar tamaño del icono para pantallas pequeñas */
  }
  .toggle-icon {
    font-size: 1.25rem; /* Ajustar tamaño del icono para pantallas pequeñas */
  }
  .course-card {
    margin-top: 1rem;
    background-color: #101223;
    padding: 1rem;
    border-radius: 8px;
  }
  .lottie-container {
    width: 100%; /* Asegurar que la animación ocupe todo el ancho */
    margin-top: 2rem; /* Espacio adicional arriba */
  }
}
</style>

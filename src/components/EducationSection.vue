<template>
  <section class="education-section">
    <div class="content">
      <h2 class="glitch" data-text="Education">Education</h2>
      <div class="education-and-animation">
        <div class="education-container">
          <div class="education-item" v-for="(education, index) in educations" :key="index" :style="{ '--i': index + 1 }">
            <h3 class="glitch" :data-text="education.degree">
              <i :class="education.degreeIcon" class="degree-icon"></i>
              {{ education.degree }}
            </h3>
            <hr>
            <p class="glitch" :data-text="education.institution">
              <i :class="education.icon" class="institution-icon"></i>
              {{ education.institution }}
            </p>
            <br>
            <p class="glitch" :data-text="education.period">{{ education.period }}</p>
            <br>
            <p class="glitch" :data-text="education.details">{{ education.details }}</p>
          </div>
        </div>
        <div class="lottie-container">
          <AnimationStudy :animationData="StudyAnimationData" />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import AnimationStudy from '@/components/Animations/AnimationStudy.vue';
import StudyAnimationData from '@/assets/AnimationStudy.json';

export default {
  name: 'EducationSection',
  components: {
    AnimationStudy,
  },
  data() {
    return {
      StudyAnimationData,
      educations: [
        {
          degree: 'Bachelor of Science in Computer Science',
          degreeIcon: 'fas fa-laptop-code',
          institution: 'Autonomus University of Aguascalientes',
          icon: 'fas fa-university',
          period: '2020 - Present',
          details: 'Relevant coursework: POO, Algorithms, Database Systems, Web Development.'
        },
        {
          degree: 'High School Diploma in Quality Control Technician',
          degreeIcon: 'fas fa-vials',
          institution: 'Conalep 1',
          icon: 'fas fa-school',
          period: '2017 - 2020',
          details: 'Activities: Math Club President, Robotics Team Captain.'
        }
      ],
    };
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;700&display=swap');

.education-section {
  background-color: #000000; /* Color de fondo oscuro */
  color: #c5c8c6; /* Color del texto */
  padding: 4rem 2rem;
  text-align: center;
  overflow: hidden;
  position: relative;
  font-family: 'Fira Code', monospace;
}

.content {
  max-width: 1200px; /* Aumenta el ancho máximo */
  margin: 0 auto;
  position: relative;
  z-index: 2;
}

.education-section h2 {
  font-size: 2.5rem;
  margin-bottom: 2rem;
  position: relative;
  color: #6DA5C0; /* Color neón */
  text-shadow: 0 0 5px #6DA5C0, 0 0 10px #6DA5C0, 0 0 20px #6DA5C0, 0 0 40px #6DA5C0, 0 0 80px #6DA5C0;
}

.education-section h2::after {
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

.education-and-animation {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}

.education-container {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  width: 60%; /* Ajusta el ancho de la sección de educación */
  position: relative;
}

.education-item {
  background-color: #1b1e34; /* Color de fondo de los ítems */
  padding: 1.5rem;
  border-radius: 8px;
  transition: transform 0.3s ease, box-shadow 0.3s ease, background-color 0.3s ease;
  border: 1px solid rgba(255, 255, 255, 0.2); /* Borde sutil */
  opacity: 0;
  transform: translateY(20px);
  animation: fadeInUp 0.6s ease forwards;
  animation-delay: calc(0.1s * var(--i));
}

.education-item:hover {
  transform: translateY(-10px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.education-item h3,
.education-item p {
  font-size: 1rem;
  color: #c5c8c6; /* Color del texto */
  margin: 0.25rem 0;
}

.degree-icon, .institution-icon {
  margin-right: 0.5rem;
  color: #6DA5C0; /* Color del icono */
  text-shadow: 0 0 5px #6DA5C0, 0 0 10px #6DA5C0, 0 0 20px #6DA5C0, 0 0 40px #6DA5C0, 0 0 80px #6DA5C0;
}

.lottie-container {
  width: 35%; /* Ajusta el ancho del contenedor de la animación */
  display: flex;
  justify-content: center;
}

@keyframes fadeInUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
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
</style>

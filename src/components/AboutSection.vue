<template>
  <section class="about-section">
    <div class="content">
      <h2>About Me</h2>
      <div class="bio">
        <p>
          I'm Donovan, a computer science student in my final year. I love challenges and constantly seek to learn new things.
        </p>
        <p>
          My main areas of interest include <span class="highlight">cybersecurity</span>, <span class="highlight">Linux systems</span>, and <span class="highlight">web development</span>.
          I enjoy exploring the depths of network security, pentesting, UNIX/LINUX system administration, and creating modern web applications.
        </p>
      </div>
      <div class="skills">
        <div class="skill">
          <i class="fas fa-shield-alt"></i>
          <h3>Cybersecurity</h3>
          <p>Passionate about protecting systems from cyber threats and ensuring data integrity.</p>
        </div>
        <div class="skill">
          <i class="fab fa-linux"></i>
          <h3>Linux</h3>
          <p>Experienced in managing and optimizing Linux servers for various applications.</p>
        </div>
        <div class="skill">
          <i class="fas fa-laptop-code"></i>
          <h3>Web Development</h3>
          <p>Skilled in building responsive and dynamic web applications using modern technologies like HTML, CSS, JavaScript, and various frameworks.</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'AboutComponent'
}
</script>

<style scoped>
.about-section {
  background-color: #000000; /* Fondo negro */
  color: #c5c8c6; /* Texto gris claro */
  padding: 4rem 2rem;
  text-align: center;
  overflow: hidden;
  position: relative;
}
.about-section::before {
  content: '';
  background-image: url('@/assets/black.jpg'); /* Logo BlackArch */
  background-size: 60%; 
  background-position: center;
  background-repeat: no-repeat;
  opacity: 0.1; 
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 1; 
}
.content {
  position: relative;
  z-index: 2; 
  max-width: 800px;
  margin: 0 auto;
}
.about-section h2 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  position: relative;
  color: #6DA5C0; /* Color del título */
  text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
}
.about-section h2::after {
  content: '';
  width: 50px;
  height: 4px;
  background-color: #6DA5C0; /* Color del subrayado */
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  box-shadow: 0 0 10px rgba(109, 165, 192, 0.5);
}
.bio {
  font-size: 1.25rem;
  line-height: 1.6;
  margin-bottom: 2rem;
  text-align: left;
}
.bio .highlight {
  color: #6DA5C0; /* Color del resaltado */
}
.skills {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
.skill {
  background-color: #1b1e34; /* Fondo gris oscuro */
  padding: 1.5rem;
  border-radius: 8px;
  width: 45%;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  margin-bottom: 1rem;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
}
.skill:hover {
  transform: translateY(-10px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.5), 0 0 10px #6DA5C0;
}
.skill i {
  font-size: 2rem;
  color: #6DA5C0; /* Icono azul */
  margin-bottom: 1rem;
  text-shadow: 0 0 10px rgba(109, 165, 192, 0.5);
}
.skill h3 {
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
  color: #ffffff;
}
.skill p {
  font-size: 1rem;
  color: #c5c8c6; /* Texto gris claro */
}
@media (max-width: 768px) {
  .skills {
    flex-direction: column;
    align-items: center;
  }
  .skill {
    width: 100%;
  }
}
</style>

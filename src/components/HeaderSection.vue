<template>
  <header class="header-section">
    <div class="content">
      <div class="left-section">
        <pre class="ascii-art" ref="asciiArt"></pre>
        <pre class="system-info">
          <span class="label">User:</span> <span class="typing" ref="user">Donovan</span>
          <span class="label">Role:</span> <span class="typing" ref="role">Computer stystems engineer student</span>
          <span class="label">Location:</span> <span class="typing" ref="location">Aguascalientes, México.</span>
          <span class="label">Skills:</span> <span class="typing" ref="skills">front-end & back-end developer</span>
          <span class="label">Contact:</span> <span class="typing" ref="contact"><a href="mailto:email@example.com">djjceja@gmail.com</a></span>
        </pre>
      </div>
      <transition name="slide-fade">
        <img v-if="visible" src="@/assets/calgary.jpg" alt="Mi Foto" class="profile-photo" />
      </transition>
    </div>
    <div class="scroll-down">
      <button @click="scrollToNextSection">
        <div class="mouse">
          <span class="arrow-down"></span>
        </div>
      </button>
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderSection',
  data() {
    return {
      visible: false,
      asciiArtLoaded: false
    };
  },
  mounted() {
    this.visible = true;
    this.loadAsciiArt();
  },
  methods: {
    async loadAsciiArt() {
      try {
        const response = await fetch('/arte-ascii.txt');
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        const asciiArt = await response.text();
        this.$refs.asciiArt.innerText = asciiArt;
        this.asciiArtLoaded = true;
        this.typeEffect(); // Start typing effect after loading ASCII art
      } catch (error) {
        console.error('Error loading ASCII art:', error);
      }
    },
    async typeEffect() {
      if (!this.asciiArtLoaded) return;

      const elements = ['user', 'role', 'location', 'skills', 'contact'];
      for (const el of elements) {
        await this.typeText(this.$refs[el], this.$refs[el].innerText);
      }
    },
    typeText(element, text) {
      return new Promise((resolve) => {
        element.innerText = '';
        let i = 0;
        const timer = setInterval(() => {
          if (i < text.length) {
            element.innerText += text.charAt(i);
            i++;
          } else {
            clearInterval(timer);
            resolve();
          }
        }, 100);
      });
    },
    scrollToNextSection() {
      const nextSection = document.querySelector('.about-section'); // Change this selector to match the next section
      if (nextSection) {
        nextSection.scrollIntoView({ behavior: 'smooth' });
      }
    }
  }
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;700&display=swap');

.header-section {
  background-color: #000000; /* Color de fondo oscuro */
  color: #c5c8c6;
  padding: 4rem 2rem;
  text-align: left;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  font-family: 'Fira Code', monospace;
  position: relative;
}
.content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  max-width: 1200px;
  width: 100%;
}
.left-section {
  display: flex;
  flex-direction: column;
}
.ascii-art {
  margin-right: 2rem;
  white-space: pre;
  color: #c5c8c6; /* Color del arte ASCII */
  text-shadow: 0 0 10px rgba(255, 255, 255, 0.3); /* Tamaño de fuente mayor */
}
.system-info {
  white-space: pre;
  color: #c5c8c6;
  font-size: 1.2rem; /* Tamaño de fuente mayor */
}
.system-info .label {
  color: #6DA5C0; /* Color actualizado */
}
.system-info a {
  color: #f39c12; /* Color actualizado */
  text-decoration: none;
}
.system-info a:hover {
  text-decoration: underline;
}
.profile-photo {
  border-radius: 50%;
  width: 300px;
  height: 300px;
  object-fit: cover;
  transition: transform 1s;
  box-shadow: 0 0 10px #6DA5C0; /* Sombra de la foto */
}
.scroll-down {
  position: absolute;
  bottom: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.scroll-down button {
  background: none;
  border: none;
  cursor: pointer;
}
.scroll-down .mouse {
  width: 24px;
  height: 40px;
  border: 2px solid #6DA5C0;
  border-radius: 15px;
  position: relative;
}
.scroll-down .mouse .arrow-down {
  position: absolute;
  bottom: 5px;
  left: 50%;
  width: 0;
  height: 0;
  margin-left: -4px;
  border-left: 4px solid transparent;
  border-right: 4px solid transparent;
  border-top: 6px solid #6DA5C0;
  animation: scrollDown 1s infinite;
}
@keyframes scrollDown {
  0% {
    opacity: 0;
    transform: translateY(0);
  }
  50% {
    opacity: 1;
  }
  100% {
    opacity: 0;
    transform: translateY(6px);
  }
}
</style>

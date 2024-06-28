<template>
  <div>
    <div class="mouse-tracker" ref="tracker"></div>
    <div v-for="(trail, index) in trails" :key="index" class="trail" :style="trail.style"></div>
  </div>
</template>

<script>
export default {
  name: 'MouseTracker',
  data() {
    return {
      trails: [],
    };
  },
  mounted() {
    document.addEventListener('mousemove', this.handleMouseMove);
  },
  beforeUnmount() {
    document.removeEventListener('mousemove', this.handleMouseMove);
  },
  methods: {
    handleMouseMove(event) {
      const tracker = this.$refs.tracker;
      tracker.style.left = `${event.clientX}px`;
      tracker.style.top = `${event.clientY}px`;

      // Add a new trail element
      const newTrail = {
        style: {
          left: `${event.clientX}px`,
          top: `${event.clientY}px`,
          opacity: 1,
        },
      };
      this.trails.push(newTrail);

      // Remove the oldest trail element after a delay
      setTimeout(() => {
        newTrail.style.opacity = 0;
      }, 50); // Start fading out almost immediately

      // Remove the element from the array after it's completely faded out
      setTimeout(() => {
        this.trails.shift();
      }, 1000);
    },
  },
};
</script>

<style scoped>
.mouse-tracker {
  width: 30px; /* Aumenta el tamaño del círculo */
  height: 30px; /* Aumenta el tamaño del círculo */
  border: 2px solid #6DA5C0; /* Borde de color neón */
  border-radius: 50%;
  position: fixed;
  pointer-events: none; /* Asegúrate de que no interfiera con los eventos de clic */
  transform: translate(-50%, -50%);
  transition: transform 0.1s ease-out;
  z-index: 1000; /* Asegura que el tracker esté por encima de otros elementos */
  background-color: transparent;
  box-shadow: 0 0 8px #6DA5C0, 0 0 16px #6DA5C0, 0 0 24px #6DA5C0;
}


</style>

<template>
    <div ref="animationContainer" class="lottie-animation"></div>
  </template>
  
  <script>
  import lottie from 'lottie-web';
  
  export default {
    name: 'AnimationStudy',
    props: {
      animationData: {
        type: Object,
        required: true,
      },
    },
    mounted() {
      this.loadAnimation();
    },
    methods: {
      loadAnimation() {
        lottie.loadAnimation({
          container: this.$refs.animationContainer,
          renderer: 'svg',
          loop: true,
          autoplay: true,
          animationData: this.animationData,
        });
      },
    },
  };
  </script>
  
  <style scoped>
  .lottie-animation {
    width: 100%;
    height: 100%;
    max-width: 500px; /* Ajusta el tamaño según tus necesidades */
    margin: 0 auto;
  }
  </style>
  
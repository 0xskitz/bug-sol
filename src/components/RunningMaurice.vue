<template>
    <div class="image-container">
      <img ref="image" src="@/assets/littleMaurice.png" alt="Example" class="moving-image">
    </div>
  </template>
  
  <script>
  export default {
    name: 'RunningMaurice',
    mounted() {
      this.startMoving();
    },
    methods: {
      startMoving() {
        this.moveImage(); // Initial move
        setInterval(this.moveImage, 3000); // Subsequent moves
      },
      moveImage() {
        const image = this.$refs.image;
        const container = this.$el;
  
        const getRandomPosition = () => {
          const x = Math.random() * (container.clientWidth + 200) - 100;
          const y = Math.random() * (container.clientHeight + 200) - 100;
          return { x, y };
        };
  
        const { x: startX, y: startY } = getRandomPosition();
        const { x: endX, y: endY } = getRandomPosition();
  
        // Set initial position and opacity
        image.style.transition = 'none';
        image.style.transform = `translate(${startX}px, ${startY}px) scale(0.5)`;
        image.style.opacity = '0';
  
        // Move to new position and fade in/out
        setTimeout(() => {
          image.style.transition = 'transform 2s ease-in-out, opacity 2s ease-in-out';
          image.style.transform = `translate(${endX}px, ${endY}px) scale(0.5)`;
          image.style.opacity = '1';
  
          // Fade out at the halfway point of the move
          setTimeout(() => {
            image.style.opacity = '0';
          }, 1000); // Start fading out halfway through the move (1000ms)
        }, 100); // Slight delay to allow initial positioning
      }
    }
  }
  </script>
  
  <style scoped>
  .image-container {
    position: fixed; /* Make the container fixed to the viewport */
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh; /* Ensure container takes full height of the viewport */
    overflow: hidden; /* Prevents image from overflowing the container */
    z-index: -1; /* Send the container to the back */
  }
  
  .moving-image {
    position: absolute;
    top: 0;
    left: 0;
    transform-origin: center; /* Ensure the scale transformation is centered */
    opacity: 0; /* Start with the image hidden */
  }
  </style>
  
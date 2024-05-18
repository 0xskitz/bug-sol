<template>
  <div class="image-container" style="align-items: center;">
    <img src="@/assets/maurice.png" alt="GM from Maurice" class="vibrating-image" @mouseover="vibrate" @mouseleave="stopVibrate">
    <div class="social-links">
      <a href="https://twitter.com/bug_sol?ref_src=twsrc%5Etfw" class="twitter-follow-button" data-show-count="false" @mouseover="vibrate" @mouseleave="stopVibrate">Follow @bug_sol</a>
      <a href="https://telegram.me/bug_sol" target="_blank" @mouseover="vibrate" @mouseleave="stopVibrate">Telegram</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MauriceComponent',
  mounted() {
      // Check if the Twitter widgets script is already loaded
      if (!window.twttr) {
        // Create a new script element
        const script = document.createElement('script');
        script.src = 'https://platform.twitter.com/widgets.js';
        script.async = true;
        script.charset = 'utf-8';
        // Append the script to the document head
        document.head.appendChild(script);
      } else {
        // If the script is already loaded, just re-render the widgets
        window.twttr.widgets.load();
      }
    },
  methods: {
    vibrate(event) {
      event.target.classList.add('vibrating');
    },
    stopVibrate(event) {
      event.target.classList.remove('vibrating');
    }
  }
}
</script>

<style scoped>
.image-container {
  display: inline-block;
  overflow: hidden; /* Ensure the image doesn't cause any overflow issues */
}

.vibrating-image {
  transition: transform 0.1s;
}

.vibrating {
  animation: vibrate 0.1s infinite;
}

@keyframes vibrate {
  0% { transform: translate(0, 0); }
  25% { transform: translate(-2px, 2px); }
  50% { transform: translate(2px, -2px); }
  75% { transform: translate(-2px, -2px); }
  100% { transform: translate(2px, 2px); }
}

.social-links {
  margin-top: 10px;
  display: flex;
  gap: 10px;
}

.social-links a {
  text-decoration: none;
  color: #1da1f2;
  font-weight: bold;
}

.social-links a:hover {
  color: #0088cc;
}
</style>

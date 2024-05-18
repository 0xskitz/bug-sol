<template>
  <div class="image-container" style="align-items: center;">
    <div v-if="hoverText" class="hover-text">{{ hoverText }}</div>
    <img src="@/assets/maurice.png" alt="GM from Maurice" class="vibrating-image" @mouseover="handleMouseOver" @mouseleave="handleMouseLeave">
    <div class="social-links">
      <a href="https://twitter.com/bug_sol?ref_src=twsrc%5Etfw" class="twitter-follow-button" data-show-count="false">Follow @bug_sol</a>
      <a href="https://telegram.me/bug_sol" target="_blank">telegram</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MauriceComponent',
  data() {
    return {
      hoverText: '',
      possibleStrings: [
        'gm',
        'we\'re all gonna make it',
        'fiat?? LOL',
        'web3 is the future',
        'buy $maurice',
        'you use fiat? ngmi',
        'brb going to the moon',
        '🚀',
        '🤑',
        'next stop: the moon',
        '9/10 doctors recommend buying $maurice',
        'the future of finance',
        'meme money magic',
        'pump it up 📈',
        'whale watch 🐋',
        'hodl',
        'wagmi',
        'ape together strong',
        '💎✊',
        'this loser didn\'t buy $maurice 🫵😂'
      ] // Add your own strings here
    };
  },
  mounted() {
      // Check if the Twitter widgets script is already loaded
      if (!window.twttr) {
        // Create a new script element
        const script = document.createElement('script');
        script.src = 'https://platform.twitter.com/widgets.js';
        script.async = true;
        // Append the script to the document head
        document.head.appendChild(script);
      } else {
        // If the script is already loaded, just re-render the widgets
        window.twttr.widgets.load();
      }
    },
  methods: {
    handleMouseOver(event) {
      this.vibrate(event);
      this.hoverText = this.getRandomString();
    },
    handleMouseLeave(event) {
      this.stopVibrate(event);
      this.hoverText = '';
    },
    vibrate(event) {
      event.target.classList.add('vibrating');
    },
    stopVibrate(event) {
      event.target.classList.remove('vibrating');
    },
    getRandomString() {
      const randomIndex = Math.floor(Math.random() * this.possibleStrings.length);
      return this.possibleStrings[randomIndex];
    }
  }
}
</script>

<style scoped>
.image-container {
  display: inline-block;
  overflow: hidden; /* Ensure the image doesn't cause any overflow issues */
  position: relative; /* Allow absolute positioning of hover text */
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

.hover-text {
  position: absolute;
  top: 0px; /* Adjust this value to position the text correctly */
  left: 50%;
  transform: translateX(-50%);
  background-color: rgba(255, 255, 255, 0.8);
  padding: 5px 10px;
  border-radius: 5px;
  font-weight: bold;
  color: #333;
  white-space: nowrap;
}
</style>

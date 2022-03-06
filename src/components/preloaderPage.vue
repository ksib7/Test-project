<template>
  <transition name="fade">
    <div v-if="isPreloaderVisible" class="preloader">
      <h2>Добро пожаловать!</h2>
      <div class="preloader__circles">
        <div class="preloader__circles__circle"></div>
        <div class="preloader__circles__circle"></div>
        <div class="preloader__circles__circle"></div>
        <div class="preloader__circles__circle"></div>
        <div class="preloader__circles__circle"></div>
        <div class="preloader__circles__circle"></div>
        <div class="preloader__circles__circle"></div>
        <div class="preloader__circles__circle"></div>
        <div class="preloader__circles__circle"></div>
        <div class="preloader__circles__circle"></div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  data() {
    return {
      isPreloaderVisible: true,
    };
  },

  mounted() {
    this.hidePreloader();
  },

  methods: {
    hidePreloader() {
      setTimeout(() => {
        this.isPreloaderVisible = false;
      }, 1000);
    },
  },
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Neonderthaw&family=Roboto+Condensed&family=Source+Sans+Pro:wght@200;400;600&display=swap");

.preloader {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background-color: white;
  z-index: 111;
}

.preloader__circles {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-top: 20px;
}

.preloader__circles__circle {
  width: 25px;
  height: 25px;
  background-color: grey;
  border-radius: 50%;
  animation-name: scaleIn;
  animation-duration: 1.7s;
  animation-name: scaleOut;
  animation-duration: 1.7s;
  transform: scale(0);
}

.preloader__circles__circle:nth-child(1) {
  animation-delay: 0s;
}

.preloader__circles__circle:nth-child(2) {
  animation-delay: 0.1s;
}

.preloader__circles__circle:nth-child(3) {
  animation-delay: 0.2s;
}

.preloader__circles__circle:nth-child(4) {
  animation-delay: 0.3s;
}

.preloader__circles__circle:nth-child(5) {
  animation-delay: 0.4s;
}

.preloader__circles__circle:nth-child(6) {
  animation-delay: 0.5s;
}

.preloader__circles__circle:nth-child(7) {
  animation-delay: 0.6s;
}

.preloader__circles__circle:nth-child(8) {
  animation-delay: 0.7s;
}

.preloader__circles__circle:nth-child(9) {
  animation-delay: 0.8s;
}

.preloader__circles__circle:nth-child(10) {
  animation-delay: 0.9s;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.preloader h2 {
  font-family: "Source Sans Pro";
  font-weight: 600;
  font-size: 62px;
  margin: 0 auto;
  color: transparent;
  background-clip: text;
  -webkit-background-clip: text;
  background-image: linear-gradient(316deg, #ffc857 0%, #3e2f5b 74%);
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

@keyframes scaleOut {
  0% {
    transform: scale(1);
  }

  100% {
    transform: scale(0);
  }
}

@keyframes scaleIn {
  0% {
    transform: scale(0);
  }

  100% {
    transform: scale(1);
  }
}
</style>

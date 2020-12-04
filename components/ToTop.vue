<template>
  <div id="toTop" :class="{ 'toTop--hidden': showToTop }">
    <img src="../assets/images/back-to-top.png" alt="back-to-top" @click="backToTop" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      showToTop: true,
      lastScrollPosition: 0,
    }
  },
  mounted() {
    window.addEventListener('scroll', this.onScroll)
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.onScroll)
  },
  methods: {
    onScroll() {
      const currentScrollPosition = window.pageYOffset || document.documentElement.scrollTop
      if (currentScrollPosition < 0) {
        return
      }
      if (Math.abs(currentScrollPosition - this.lastScrollPosition) < 50) {
        return
      }
      this.showToTop = currentScrollPosition < this.lastScrollPosition
      this.lastScrollPosition = currentScrollPosition
    },
    backToTop() {
      document.body.scrollTop = 0
      document.documentElement.scrollTop = 0
    },
  },
}
</script>

<style lang="scss">
//? Styling
#toTop {
  color: chocolate;
  z-index: 5000;
  width: 50px;
  height: 50px;
  cursor: pointer;
  position: fixed;
  bottom: 50px;
  right: 50px;
  transform: translate3d(0, 0, 0);
  transition: 0.3s all ease-out;
  img {
    width: 50px;
    height: 50px;
  }
}
#toTop:hover {
  animation-name: animations-Jump-Up;
  animation-duration: 0.6s;
  animation-delay: -0.08s;
  transition: 0.3s all ease-out;

  transform: translate3d(0, -10%, 0);
}
#toTop.toTop--hidden {
  box-shadow: none;
  transform: translate3d(0, 100%, 0);
  bottom: -50px;
}

//? Queries
@media screen and (max-width: 800px) {
  #toTop {
    z-index: 0;
  }
}

//? Animations
@keyframes animations-Jump-Up {
  100% {
    transform: translate3d(0, -10%, 0);
  }
}
</style>

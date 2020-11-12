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

      if (window.innerHeight + window.scrollY >= document.body.offsetHeight + 50) {
        this.showToTop = false
        document.getElementById('toTop').style.transition = '0.01s all ease-out;'
        document.getElementById('toTop').style.transition = '0.3s all ease-out;'
      } else {
        if (currentScrollPosition < 0) {
          return
        }
        if (Math.abs(currentScrollPosition - this.lastScrollPosition) < 50) {
          return
        }
        this.showToTop = currentScrollPosition < this.lastScrollPosition
        this.lastScrollPosition = currentScrollPosition
      }
    },
    backToTop() {
      document.body.scrollTop = 0
      document.documentElement.scrollTop = 0
    },
  },
}
</script>

<style lang="scss">
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

  transform: translate3d(0, -24%, 0);
}
#toTop.toTop--hidden {
  box-shadow: none;
  transform: translate3d(0, 100%, 0);
  bottom: -50px;
}
@keyframes animations-Jump-Up {
  0% {
    transition: 0.4s all ease-out;
    transform: translate3d(0, -18%, 0);
  }
  25% {
    transition: 0.3s all ease-out;
    transform: translate3d(0, 16%, 0);
  }
  50% {
    transition: 0.3s all ease-out;
    transform: translate3d(0, -18%, 0);
  }
  75% {
    transform: translate3d(0, 22%, 0);
  }
  100% {
    transform: translate3d(0, -24%, 0);
  }
}
@media screen and (max-width: 800px) {
  #toTop {
    z-index: 0;
  }
}
</style>

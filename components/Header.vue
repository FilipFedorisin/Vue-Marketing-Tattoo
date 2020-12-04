<template>
  <div class="container" :class="{ 'container--hidden': !showContainer }">
    <div id="Navbar">
      <div id="Logo">
        <img src="../assets/images/logo.png" alt="logo" />
      </div>
      <div v-show="!hamburger" id="Navigation">
        <span>Domov</span>
        <span>Služby</span>
        <span>Galéria</span>
        <span>Kontakt</span>
      </div>
      <Hamburger v-show="hamburger" />
    </div>
  </div>
</template>

<script>
import Hamburger from '../components/Hamburger.vue'

export default {
  components: {
    Hamburger,
  },
  data() {
    return {
      showContainer: true,
      lastScrollPosition: 0,
      hamburger: false,
    }
  },
  mounted() {
    window.addEventListener('scroll', this.onScroll)
    window.addEventListener('resize', this.showHam)
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.onScroll)
    window.removeEventListener('resize', this.showHam)
  },
  methods: {
    onScroll() {
      const currentScrollPosition = window.pageYOffset || document.documentElement.scrollTop
      if (window.innerHeight + window.scrollY >= document.body.offsetHeight - 50) {
        this.showContainer = true
      } else {
        if (currentScrollPosition < 0) {
          return
        }
        if (Math.abs(currentScrollPosition - this.lastScrollPosition) < 50) {
          return
        }
        this.showContainer = currentScrollPosition < this.lastScrollPosition
        this.lastScrollPosition = currentScrollPosition
      }
    },
    showHam() {
      if (window.innerWidth < 800) {
        this.hamburger = true
      } else {
        this.hamburger = false
      }
    },
  },
}
</script>

//? Styling
<style lang="scss" scoped>
.container {
  z-index: 50;
  position: fixed;
  transform: translate3d(0, 0, 0);
  transition: 0.15s all ease-out;
  background-color: black;
  height: 50px;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;

  #Navbar {
    display: flex;
    justify-content: space-between;
    align-content: center;
    align-items: center;
    height: 50px;
    min-width: 1000px;
    max-width: 1300px;

    #Logo {
      display: flex;
      align-items: center;
      width: 30%;
      transform: translate3d(0, 0, 0);
      transition: 0.1s all ease-out;

      img {
        cursor: pointer;
        padding-top: 10px;
        height: 70px;
        width: 130px;
      }
    }
    #Navigation {
      display: flex;
      align-items: center;
      justify-content: space-between;
      width: 50%;
      height: 50px;
      color: white;
      transform: translate3d(0, 0, 0);
      transition: 0.3s all ease-out;

      span {
        font-family: 'Montserrat', sans-serif;
        line-height: 38px;
        cursor: pointer;
        text-align: center;
        width: 20%;
      }
      span:hover {
        color: $colors-Burnt-Sienna;
        background-color: rgba(255, 255, 255, 0.1);
        transition: all 0.3s ease;
        animation-name: animations-Pop-Up;
        animation-duration: 0.5s;
        animation-delay: -0.1s;
        transition: transform 0.3s ease-out;
        border-radius: 12px;
        border-style: solid;
        border-width: 1px;
        box-shadow: 0 0 4px $colors-Burnt-Sienna;
      }
    }
  }
}
.container.container--hidden {
  box-shadow: none;
  transform: translate3d(0, -100%, 0);

  #Navbar {
    #Logo {
      transition: 0.3s all ease-out;
      transform: translate3d(0, 100%, 0);
    }
  }
}

//? Queries
@media screen and (max-width: 1000px) {
  .container {
    #Navbar {
      min-width: 100%;
    }
  }
}

//? Animations
@keyframes animations-Pop-Up {
  50% {
    border-radius: 2px;
    border-width: 4px;
  }
  60% {
    border-radius: 3px;
    border-width: 3px;
  }
  70% {
    border-radius: 5px;
    border-width: 2px;
  }
  80% {
    border-radius: 8px;
    border-width: 1.5px;
  }
  90% {
    border-radius: 10px;
    border-width: 1.2px;
  }
  100% {
    border-radius: 12px;
    border-width: 1.1px;
  }
}
</style>

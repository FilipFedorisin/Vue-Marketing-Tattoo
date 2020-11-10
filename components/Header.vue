<template>
  <div class="container" :class="{ 'container--hidden': !showContainer }">
    <div id="Navbar">
      <div id="Logo">
        <img src="../assets/images/logo.png" alt="logo" />
      </div>
      <div id="Navigation">
        <span>Domov</span>
        <span>Služby</span>
        <span>Galéria</span>
        <span>Kontakt</span>
      </div>
      <div id="toTop" :class="{ 'toTop--hidden': showToTop }">
        <img src="../assets/images/back-to-top.png" alt="back-to-top" @click="backToTop" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showContainer: true,
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

      if (window.innerHeight + window.scrollY >= document.body.offsetHeight) {
        this.showContainer = true
        this.showToTop = false
        document.getElementById('toTop').style.transition = '0.01s all ease-out;'
        document.getElementById('toTop').style.bottom = 'calc((100vh - 100px) * -1)'
        document.getElementById('toTop').style.transition = '0.3s all ease-out;'
      } else {
        document.getElementById('toTop').style.bottom = 'calc((100vh - 50px) * -1)'
        if (currentScrollPosition < 0) {
          return
        }
        if (Math.abs(currentScrollPosition - this.lastScrollPosition) < 50) {
          return
        }
        this.showContainer = currentScrollPosition < this.lastScrollPosition
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
      //margin-top: 10px;

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
        //transform: scale(1.1);
        border-radius: 12px;
        border-style: solid;
        border-width: 1px;
        box-shadow: 0 0 4px $colors-Burnt-Sienna;
      }
    }
    #toTop {
      width: 50px;
      height: 50px;
      cursor: pointer;
      position: fixed;
      bottom: calc((100vh - 50px) * -1);
      right: 50px;
      transform: translate3d(0, 0, 0);
      transition: 0.3s all ease-out;

      img {
        width: 50px;
        height: 50px;
      }
    }
    #toTop:hover {
      transform: translate3d(0, -18%, 0);
    }
    #toTop.toTop--hidden {
      box-shadow: none;
      transform: translate3d(0, 100%, 0);
    }
  }
  @media screen and (max-width: 1000px) {
    #Navbar {
      max-width: 1000px;
      min-width: 100%;
      display: grid;
      justify-content: center;
      justify-items: start;
      grid-template-columns: repeat(auto-fit, minmax(164px, 1fr));

      grid-auto-rows: max-content;
      row-gap: 15px;
      height: auto;
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

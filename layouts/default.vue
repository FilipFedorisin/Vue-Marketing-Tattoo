<template>
  <div>
    <Header />
    <ToTop />
    <Nuxt id="NUXT" />
    <Footer />
  </div>
</template>

<script>
import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'
import ToTop from '../components/ToTop.vue'

export default {
  components: {
    Header,
    Footer,
    ToTop,
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Vollkorn&display=swap');
/*
  font-family: 'Vollkorn', serif; 
*/

@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@500&display=swap');
/* 
  font-family: 'Montserrat', sans-serif;
*/

#app {
  font-family: 'Vollkorn', serif;
  font-size: 20px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}
::-webkit-scrollbar {
  width: 5px;
  height: 6px;
}
/* Track */
::-webkit-scrollbar-track {
  background: black;
}
/* Handle */
::-webkit-scrollbar-thumb {
  -webkit-border-radius: 0px;
  border-radius: 0px;
  background: #e76f51;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

#NUXT {
  border-top: 50px;
}
</style>

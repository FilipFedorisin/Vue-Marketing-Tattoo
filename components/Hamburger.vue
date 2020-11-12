<template>
  <div class="hamburgerMenuComponent">
    <img class="hamIcon" src="../assets/images/hamburger.png" @click="showHamMenu" />
    <div id="hamMenu">
      <a>Domov</a>
      <a>Služby</a>
      <a>Galéria</a>
      <a>Kontakt</a>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    showHamMenu() {
      const dropdown = document.getElementById('hamMenu')
      if (dropdown.style.display === 'block') {
        dropdown.style.display = 'none'
      } else {
        dropdown.style.display = 'block'
      }
    },
  },
}
</script>

<style lang="scss" scoped>
.hamburgerMenuComponent {
  .hamIcon {
    display: block;
    width: 50px;
    height: 50px;
    background-color: black;
  }

  #hamMenu {
    display: none;
    position: absolute;
    width: 100px;
    margin-left: -50px;
    background-color: black;
  }

  a {
    color: white;
    padding: 14px 16px;
    text-decoration: none;
    font-size: 17px;
    display: block;
  }
}
</style>

<template>
  <footer>
    <div class="container">
      <div class="social-media">
        <span>Sociálne Média</span>
        <img id="facebook" src="../assets/images/facebook.png" alt="facebook" />
        <img id="instagram" src="../assets/images/instagram.png" alt="instagram" />
      </div>
      <div class="help-and-support">
        <span>Zákaznická podpora</span>
        <ul>
          <li>Ako sa objednať</li>
          <li>Špeciálne požiadavky</li>
          <li>Kontakt</li>
        </ul>
      </div>
      <div class="site-map">
        <span>Mapa Stránky</span>
        <ul>
          <li>Domov</li>
          <li>Služby</li>
          <li>Galéria</li>
          <li>Kontakt</li>
        </ul>
      </div>
      <div class="documents">
        <span>Dokumenty</span>
        <ul>
          <li>Cookies</li>
          <li>GDPR</li>
        </ul>
      </div>
    </div>
    <span id="tag">All rights reserved 2020. Filip Fedorišin,</span>
  </footer>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
footer {
  z-index: 10;
  position: sticky;
  top: calc(100vh - 250px);
  color: white;
  height: 200px;
  background-color: black;
  display: flex;
  justify-content: center;
  align-items: center;

  .container {
    max-width: 1000px;
    min-width: 1000px;

    display: grid;
    grid-template-columns: repeat(4, minmax(max-content, max-content));
    grid-auto-rows: max-content;
    justify-items: center;
    justify-content: space-between;

    .social-media {
      img {
        display: inline-block;
        margin-right: 15px;
        width: 32px;
        height: 32px;
        cursor: pointer;
      }
      img:hover {
        background-color: rgba(255, 255, 255, 0.1);
        transition: all 0.3s ease;
        animation-name: animations-Pop-Up;
        animation-duration: 0.5s;
        animation-delay: -0.1s;
        transform: scale(1.1);
        border-radius: 12px;
      }
    }

    ul {
      list-style-type: none;
      margin: 0;
      padding: 0;
    }
    li {
      padding-top: 2px;
      padding-bottom: 2px;
      padding-left: 5px;
      cursor: pointer;
    }
    li:hover {
      color: $colors-Burnt-Sienna;
    }
    a {
      text-decoration: none;
      color: white;
    }
    span {
      color: $colors-Burnt-Sienna;
      display: block;
      padding: 4px;
      cursor: pointer;
      font-family: 'Montserrat', sans-serif;
    }
    span:hover {
      color: $colors-Burnt-Sienna;

      background-color: rgba(255, 255, 255, 0.1);
      transition: all 0.3s ease;
      animation-name: animations-Pop-Up;
      animation-duration: 0.5s;
      animation-delay: -0.1s;
      transform: scale(1.1);
      border-radius: 12px;
    }
  }
  #tag {
    position: fixed;
    bottom: calc((100vh - 50px) * -1);
  }

  @media screen and (max-width: 1000px) {
    .container {
      max-width: 1000px;
      min-width: 0px;
      justify-content: center;
      justify-items: start;
      .social-media,
      .help-and-support,
      .site-map,
      .documents {
        padding-left: 20%;
      }
      grid-template-columns: repeat(auto-fit, minmax(164px, 1fr));

      grid-auto-rows: max-content;
      row-gap: 15px;
    }
    height: auto;
    padding-bottom: 50px;
  }
}

@keyframes animations-Pop-Up {
  0% {
    transition: 0.2s all ease-out;
  }
  10% {
    transform: scale(1.01);
  }
  20% {
    transform: scale(1.04);
  }
  30% {
    transform: scale(1.05);
  }
  40% {
    transform: scale(1.08);
  }
  50% {
    border-radius: 2px;
  }
  60% {
    border-radius: 3px;
  }
  70% {
    border-radius: 5px;
  }
  80% {
    border-radius: 8px;
  }
  90% {
    border-radius: 10px;
  }
  100% {
    border-radius: 12px;
  }
}
</style>

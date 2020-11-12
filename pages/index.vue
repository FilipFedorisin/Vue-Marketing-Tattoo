<template>
  <div class="container">
    <div id="Index">
      <p id="Easter-Egg">rýchlosť svetla</p>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.container {
  background-color: rgb(54, 54, 54);
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;

  #Index {
    padding-top: 28px;
    background-color: whitesmoke;
    height: 200vh;
    min-width: 1000px;
    max-width: 1000px;
    text-align: center;

    #Easter-Egg {
      color: $colors-Burnt-Sienna;
    }
  }
  @media screen and (max-width: 1000px) {
    #Index {
      min-width: 100%;
      /*
      display: grid;
      justify-content: center;
      justify-items: start;
      grid-template-columns: repeat(auto-fit, minmax(164px, 1fr));
      grid-auto-rows: max-content;
      row-gap: 15px;
      height: auto;
      */
    }
  }
}
</style>

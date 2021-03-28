<template>
  <div class="Default">
    <Header/>
    <Nuxt/>
  </div>
</template>

<style lang="scss">
@import "assets/styles/font";


.Default {
  display: grid;
  grid-template-columns: 80px 1fr;
  height: 100vh;
  @media (max-width: 620px) {
    grid-template-columns: 1fr;
  }
}


html {
  font-family: MyEurope, serif;
  background-color: #FBFBFB;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
  font-family: MyEurope, serif;
}


</style>
<script>
import Header from "@/components/Header";

export default {
  components: {Header}
}
</script>

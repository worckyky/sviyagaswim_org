<template>
  <router-link :to="route" class="Button">
    <slot/>
  </router-link>
</template>

<script>
  export default {
    props: {
      route: {
        default: '/'
      }
    }
  }
</script>

<style scoped lang="scss">
@import "assets/styles/variables";
  .Button {
    padding: 16px 24px;
    background-color: $yellow;
    color: $black;
    font-size: 20px;
    line-height: 24px;
    text-decoration: none;
    width: fit-content;
  }
</style>

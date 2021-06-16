<template>
  <a :href="route" class="Button" target="_blank">
    <slot/>
  </a>
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
    border: 1px solid $yellow;
    color: $white;
    border-radius: 6px;
    font-size: 20px;
    display: inline-block;
    line-height: 24px;
    text-decoration: none;
    width: fit-content;
    -webkit-transition: ease-in-out 0.2s;
    -moz-transition: ease-in-out 0.2s;
    -ms-transition: ease-in-out 0.2s;
    -o-transition: ease-in-out 0.2s;
    transition: ease-in-out 0.2s;
    &:hover {
      background-color: transparent;
      border: 1px solid $yellow;
      color: $yellow;
    }
    @media (max-width: 475px) {
      padding: 12px 16px;
      font-size: 16px;
    }
  }
</style>

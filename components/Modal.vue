<template>
  <div class="Modal" @click="hideModal">
    <div class="Modal__container" :class="isShown && 'animation'">
      <div class="Modal__head">
        <p>{{title}}</p>
        <img src="~/assets/images/Events/Close.svg" alt="" class="hide">
      </div>
      <div class="Modal__container-wrapper">
        <slot/>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Modal',
  props: {
    title: {
      default: 'Заголовок'
    }
  },
  data() {
   return {
     isShown: false
   }
  },
  methods: {
    hideModal(e) {
      if (['hide', 'Modal'].includes(e.target.className)) {
        this.$emit('hide',)
        this.isShown = false;
      }
    },
  },
  mounted() {
    this.isShown = true;
  }
}
</script>

<style lang="scss" scoped>
@import "assets/styles/mixins";
@import "assets/styles/variables";

.Modal {
  position: fixed;
  right: 0;
  top: 0;
  width: 100%;
  height: 100%;
  z-index: 1000;
  align-items: center;
  justify-content: center;
  display: flex;
  background: rgba(0, 0, 0, 0.6);

  &__container {
    background-color: #fff;
    width: 700px;
    height: 400px;
    border-radius: 10px;
    overflow: hidden;
    margin: 16px;
    &-wrapper {
      position: relative;
      width: 100%;
      height: 100%;
      padding: 24px;
      .video {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 87%;
      }
    }

  }
  .animation {
    animation: 0.4s ease 0s 1 normal forwards running animation;
    transform-origin: 50% 50%
  }
  @keyframes animation {
    0% {
      transform: translateY(0px);
      opacity: 0;
    }
    100% {
      transform: translateY(-40px);
      opacity: 1;
    }
  }
  &__head {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 56px;
    padding: 0 24px;
    border-bottom: 1px solid $gray300;

    img {
      cursor: pointer;
      width: 24px;
    }
  }
}
</style>

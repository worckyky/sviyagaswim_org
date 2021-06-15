<template>
  <div class="Social">
    <div class="Social__container">
      <h2 class="Social__title">Новости</h2>
      <p class="Social__paragraph">Подписывайся на наши социальные сети, чтобы быть в курсе новостей, изменений и
        конкурсов от наших партнеров</p>
      <div class="Social__links">
        <a
          v-for="(elem, i) of Social"
          :key="i"
          :href="elem.link"
        >
          <img :src="require(`~/assets/images/Social/Icons/${elem.icon}.svg`)" alt="">
        </a>
      </div>
    </div>
  </div>
</template>


<script>
import social from "assets/content/social";
export default {
  data() {
    return {
      Social: social
    }
  }
}
</script>

<style scoped lang="scss">
@import "assets/styles/mixins";
@import "assets/styles/variables";

.Social {
  position: relative;
  background-image: url("assets/images/Social/Bg.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  z-index: 0;
  margin: 24px;
  border-radius: 5px;
  overflow: hidden;
  @include imageShadow;

  &::after {
    content: '';
    z-index: -1;
    position: absolute;
    top: 0;
    right: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.4);
  }

  &__container {
    @include layout;
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
    color: $white;
  }

  &__title {
    @include titleH2;
    color: $white;
    margin-top: 80px;
  }

  &__paragraph {
    max-width: 556px;
    padding: 0 16px;
    font-size: 18px;
    line-height: 28px;
    margin: 0 auto;
    margin-bottom: 32px;
  }

  &__links {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin: 0 auto;
    margin-bottom: 80px;
    max-width: 556px;
    a {
      margin: 16px;
      @media (max-width: 480px) {
        flex-basis: 26%;
      }
      img {
        width: 72px;
      }
    }
  }
}

</style>

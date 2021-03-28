<template>
  <div class="Expo">
    <div class="Expo__container">
      <div class="Expo__info">
        <div class="Expo__data">
          <p>30 апреля - 1 мая</p>
          <h2 class="Expo__title">
            Спортивная выставка
          </h2>
          <a href="">
            <img src="~/assets/images/Expo/Document.svg" alt="">
            Скачать схему экспо
          </a>
        </div>
        <div class="Expo__features">
          <div class="Expo__features-element" v-for="(elem, i) of features">
            <img
              :key="i"
              :src="require(`~/assets/images/Expo/Features/${elem.img}.svg`)" alt="">
            <p>{{ elem.text }}</p>
          </div>
        </div>
      </div>
      <div class="Expo__question">
        По вопросам учаcтия  спортивной выставки в качестве экспонента обращаться на почту <span><a href="mailto:partner@timerman.org" class="link">partner@timerman.org</a></span>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      features: [
        {
          img: 'shop',
          text: 'Спортивные бренды и представители индустрии'
        },
        {
          img: 'muscle',
          text: 'Углеводная загрузка на Parta Party'
        },
        {
          img: 'flag',
          text: 'Парад регионов'
        }, {
          img: 'kid',
          text: 'Детские зоны и забег ползунков'
        }, {
          img: 'book',
          text: 'Лекторий, на котором обсудят актуальные вопросы спортивного сообщества'
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
@import "assets/styles/mixins";
@import "assets/styles/variables";

.Expo {
  padding: 56px 0;
  &__container {
    @include layout;
    display: flex;
    flex-direction: column;
  }
  &__info, {
    display: flex;
    @media (max-width: 920px) {
      flex-direction: column;
    }
  }

  &__data, &__features {
    width: 50%;
    @media (max-width: 920px) {
      width: 100%;
    }
  }
  &__title {
    @include titleH2;
    color: $white;
  }
  &__question {
    padding: 32px;
    font-size: 18px;
    line-height: 28px;
    text-align: center;
    background-color: $white;
    @include imageShadow;
    a {
      color: $black;
      position: relative;
      text-decoration: none;
      &::after {
        content: '';
        display: block;
        position: absolute;
        bottom: -2;
        right: 0;
        width: 100%;
        background-color: $yellow;
        height: 3px;
      }
    }
  }
  &__features {
    background-color: $yellow;
    padding: 32px 24px;
    @media (max-width: 920px) {
      display: flex;
      flex-direction: column;
    }
    &-element {
      display: flex;
      align-items: center;
      margin-bottom: 32px;
      @media (max-width: 480px) {
        flex-direction: column;
        justify-content: center;
        text-align: center;
        width: 100%;
      }
      &:nth-last-child(1) {
        margin-bottom: 0;
      }
      p {
        margin-left: 24px;
        font-size: 18px;
        line-height: 28px;
        color: $black;
        @media (max-width: 480px) {
          margin-left: initial;
        }
      }
    }
  }

  &__data {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-image: url("~/assets/images/Expo/Bg.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    z-index: 0;
    position: relative;
    color: $white;
    p {
      margin-bottom: 32px;
      text-transform: uppercase;
    }
    &::after {
      content: '';
      z-index: -1;
      position: absolute;
      top: 0;
      right: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.6);
    }
    a {
      margin-top: 48px;
      display: flex;
      align-items: center;
      width: fit-content;
      text-decoration: none;
      color: $white;
      img{
        margin-right: 16px;
        width: 40px;
      }
    }
    @media (max-width: 920px) {
      padding: 56px 0;
    }
  }
}
</style>

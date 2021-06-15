<template>
  <div class="Live" id="main">
    <div class="Live__container">
      <div class="Live__title">
        <h2>Где жить</h2>
      </div>
      <div class="Live__features">
        <div class="Live__features-elem" v-for="(e, i) of features" :key="i">
          <div class="Live__features-img">
            <img :src="require(`~/assets/images/Live/${e.icon}.svg`)" alt="">
          </div>
          <div class="Live__features-content">
            <div v-if="e.icon === 'hotel'">
              <p>
                <a href="https://sviyagaclub.ru/" target="_blank">Загородный клуб “Свияга”</a>
              </p>
              <p>
                (8 минут до острова на машине)
              </p>
              <p>
                <a href="https://sviyaga-hills.com/" target="_blank">Город-курорт “Свияжские холмы” </a>
              </p>
              <p>(45 минут на машине)</p>
              <p> отели Казани</p>
              <p>(1-2 часа на машине)</p>
            </div>
            <p v-else> {{ e.description }}</p>
          </div>
        </div>
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
          icon: 'tent',
          description: 'На территории острова будет организован палаточный городок. Приезжайте со своей палаткой, возьмите у знакомых или арендуйте и наслаждайтесь природой острова!  Романтика!'
        },
        {
          icon: 'trailer',
          description: 'Недалеко от въезда на Свияжск будет организована стоянка для трейлеров. Размещение бесплатное.'
        },
        {
          icon: 'hotel',
          description: 'Загородный клуб “Свияга” (8 минут до острова на машине)\n' +
            'город-курорт “Свияжские холмы” (45 минут на машине) \n' +
            'отели Казани (1-2 часа на машине)'
        },
      ]
    }
  }
}
</script>


<style lang="scss" scoped>
@import "assets/styles/mixins";
@import "assets/styles/variables";

.Live {
  padding: 80px 0;
  background-color: $white;

  &__container {
    @include layout;
  }

  &__title {
    grid-column: 1 / 3;
    display: flex;
    align-items: center;
    h2 {
      @include titleH2;
    }
    @media (max-width: 756px) {
      grid-column: 1 / 13;
      grid-row: 1;
      margin-bottom: 32px;
      justify-content: center;
    }
  }

  &__features {
    grid-column: 3 / 13;
    display: flex;
    flex-wrap: wrap;
    @media (max-width: 756px) {
      grid-column: 1 / 13;
      grid-row: 2;
    }
    &-img {
      position: absolute;
      background-color: $white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      width: 60px;
      height: 60px;
      @include imageShadow;
      top: -30px;
      left: 16px;

      img {
        width: 32px;
      }

      @media (max-width: 475px) {
        left: unset;
      }
    }

    &-elem {
      flex-basis: 270px;
      min-height: 230px;
      @include imageShadow;
      margin-bottom: 48px;
      background-color: $white;
      border-radius: 6px;
      margin-right: 24px;

      &:nth-last-child(1) {
        margin-right: unset;
      }
      @media (max-width: 756px) {
        flex-basis: 45%;
      }
      @media (max-width: 475px) {
        flex: 100%;
        display: flex;
        margin-left: unset;
        align-items: center;
        justify-content: center;
        height: 146px;
        margin-right: unset;
        min-height: 200px;
      }

    }

    &-content {
      order: 1;
      padding: 48px 16px 16px 16px;
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;

      h3 {
        font-family: Swiyaga, Serif;
        font-size: 18px;
        line-height: 24px;
        text-transform: uppercase;
      }

      p {
        font-size: 14px;
        line-height: 22px;
      }
      a {
        color: $yellow;
        text-decoration: none;
      }
      @media (max-width: 475px) {
        text-align: center;
      }
    }
  }
}
</style>

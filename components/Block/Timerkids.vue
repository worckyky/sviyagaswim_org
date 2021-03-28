<template>
  <div class="Timerkids" id="Timerkids">
    <div class="Timerkids__container">
      <div class="Timerkids__slider">
        <div class="Timerkids__slider-navigation">
          <img src="~/assets/images/NewYear/Slider/navigation/left.svg" @click="prevSlide" alt="left">
          <img src="~/assets/images/NewYear/Slider/navigation/right.svg" @click="nextSlide" alt="right">
        </div>
        <Carousel
          :navigation-enabled="sliderConfig.navigationEnabled"
          :pagination-enabled="sliderConfig.paginationEnabled"
          :navigation-next-label="sliderConfig.nextLabel"
          :navigation-prev-label="sliderConfig.prevLabel"
          :autoplay="sliderConfig.autoplay"
          :per-page="sliderConfig.perPage"
          :autoplay-timeout="sliderConfig.autoplayTimeout"
          :loop="sliderConfig.loop"
          :speed="sliderConfig.speed"
          :paginationColor="sliderConfig.paginationColor"
          :paginationActiveColor="sliderConfig.paginationActiveColor"
          ref="carousel"
        >
          <Slide v-for="(slide , i) in photos" :key="i">
            <div class="Timerkids__slider-block">
              <div
                class="element"
                :style="{ 'background-image': `url(${imgAddress(slide)})` }"
              ></div>
<!--              <img :src="require(`~/assets/images/NewYear/Slider/${slide}.jpg`)" alt="image"-->
<!--              >-->
            </div>
          </Slide>
        </Carousel>
      </div>
      <div class="Timerkids__content">
        <img src="~/assets/images/Timerkids/Timer_logo.svg" alt="">
        <p>Чтобы ребенок рос здоровым и физически развитым, важно с детства прививать любовь к спорту. </p>
        <p>Наши соревнования рассчитаны на различные возрастные категории и уровень подготовки детей.</p>
      </div>
    </div>
  </div>
</template>

<script>
import Modal from "@/components/Modal";
import {Carousel, Slide} from "vue-carousel";

export default {
  components: {
    Carousel,
    Slide,
  },
  data() {
    return {
      photos: ['1', '2', '3'],
      sliderConfig: {
        autoplay: true,
        perPage: 1,
        autoplayTimeout: 4000,
        loop: true,
        direction: 'forward',
        paginationPosition: ['overlay', 'bottom-overlay'],
        speed: 1000,
        paginationEnabled: true,
        paginationColor: '#D1D1D1',
        paginationActiveColor: '#F7C24D',
      },
    }
  },
  methods: {
    imgAddress(number) {
      return require(`~/assets/images/Timerkids/Photos/${number}.jpg`)
    },
    nextSlide() {
      this.$refs.carousel.goToPage(this.$refs.carousel.getNextPage());
    },
    prevSlide() {
      this.$refs.carousel.goToPage(this.$refs.carousel.getPreviousPage());
    }
  }
}
</script>


<style lang="scss" scoped>
@import "assets/styles/mixins";
@import "assets/styles/variables";

.Timerkids {
  &__container {
    @include layout;
    @media (max-width: 920px) {
      grid-template-rows: repeat(2, auto);
      grid-template-columns: repeat(4 ,1fr);
    }
  }

  &__slider {
    grid-column: 1 / 7;
    position: relative;
    @media (max-width: 920px) {
      grid-column: 1 / 5;
      grid-row: 1;
      display: flex;
      flex-direction: column;
    }
    &-navigation {
      display: flex;
      justify-content: space-between;
      z-index: 10;
      top: 177px;
      position: relative;
      cursor: pointer;
      @media (max-width: 920px) {
        grid-column: 1 / 5;
        grid-row: 1;
        top: 206px;
      }
      @media (max-width: 768px) {
        top: auto;
        position: absolute;
        width: 100%;
        bottom: -9px;
      }
    }
    &-block {
      display: flex;
      justify-content: center;
      .element {
        width: 380px;
        height: 300px;
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;
        @media (max-width: 920px) {
          width: 500px;
          height: 360px;
        }
        @media (max-width: 768px) {
          width: 100%;
          height: 360px;
        }
      }
    }
  }
  &__content {
    grid-column: 7 / 13;
    font-size: 18px;
    line-height: 28px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    @media (max-width: 920px) {
      grid-column: 1 / 5;
      grid-row: 2;
      align-items: center;
      text-align: center;
    }
    img {
      width: 165px;
      margin-bottom: 32px;
    }
    p {
      margin-bottom: 24px;
    }
  }
}
</style>

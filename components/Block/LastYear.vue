<template>
  <div class="LastYear">
    <div class="LastYear__container">
      <div class="LastYear__video"
           >
        <h1 class="LastYear__title">
          Как это было в прошлом году
        </h1>
        <div class="LastYear__video-container" @click="showModal">
            <img src="~/assets/images/NewYear/Play.svg" alt="">
        </div>
      </div>
      <div class="LastYear__slider">
        <div class="LastYear__slider-navigation">
          <img src="~/assets/images/NewYear/Slider/navigation/left.svg" @click="prevSlide" alt="left">
          <img src="~/assets/images/NewYear/Slider/navigation/right.svg" @click="nextSlide" alt="right">
        </div>
        <div class="LastYear__slider-container">
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
            <Slide v-for="(slide , i) in screens" :key="i">
              <div class="LastYear__slider-block">
                <img :src="require(`~/assets/images/NewYear/Slider/${slide}.jpg`)" alt="image"
                >
              </div>
            </Slide>
          </Carousel>
        </div>
      </div>
      <Modal @hide="show = false" v-if="show"/>
    </div>
  </div>
</template>

<script>
import Modal from "@/components/Modal";
import {Carousel, Slide} from 'vue-carousel'

export default {
  components: {
    Modal, Carousel,
    Slide,
  },
  data() {
    return {
      show: false,
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
        paginationActiveColor: '#F7C24D'
      },
      screens: [
        '1',
        '2',
        '3'
      ]
    }
  },
  methods: {
    showModal() {
      this.show = true
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


<style scoped lang="scss">
@import "assets/styles/mixins";
@import "assets/styles/variables";

.LastYear {
  background-color: $white;
  padding: 80px 0;
  @media (max-width: 756px) {
    padding-bottom: 120px;
  }
  &__container {
    @include layout;
    @media (max-width: 756px) {
      grid-template-rows: auto auto;
      grid-row-gap: 48px;
    }
  }

  &__title {
    @include titleH2;
    margin-bottom: 80px;
    @media (max-width: 756px) {
      text-align: center;
      margin-bottom: 48px;
    }
  }

  &__slider {
    grid-column: 7 / 13;
    display: flex;
    justify-content: center;
    position: relative;
    @media (max-width: 920px) {
      grid-column: 5/9;
    }
    @media (max-width: 756px) {
      grid-row: 2;
      grid-column: 1/9;
    }
    &-navigation {
      position: absolute;
      bottom: 230px;
      width: 90%;
      display: flex;
      justify-content: space-between;
      z-index: 10;


      img {
        cursor: pointer;
      }
      @media (max-width: 756px) {
        bottom: -66px;
      }
    }

    &-container {
      height: 500px;
      width: 400px;
      position: relative;
      @media (max-width: 920px) {
        width: 80%;
      }
    }

    &-block {
      display: flex;
      justify-content: center;
    }
  }

  &__video {
    grid-column: 1 / 7;
    @media (max-width: 920px) {
      grid-column: 1/5;
    }
    @media (max-width: 756px) {
      grid-row: 1;
      grid-column: 1/9;
    }

    &-container {
      cursor: pointer;
      height: 300px;
      background-image: url("assets/images/NewYear/VideoPreview.jpg");
      z-index: 0;
      position: relative;
      @include imageShadow;
      display: flex;
      align-items: center;
      justify-content: center;
      @media (max-width: 480px) {
        height: 200px;
      }
      &::after {
        cursor: pointer;
        content: '';
        z-index: -1;
        position: absolute;
        top: 0;
        right: 0;
        width: 100%;
        height: 100%;
        background: rgba(196, 196, 196, 0.091);
        box-shadow: inset 28.6px -28.6px 28.6px rgba(149, 149, 149, 0.091), inset -28.6px 28.6px 28.6px rgba(255, 255, 255, 0.091);
        backdrop-filter: blur(6.864px);
      }
    }
  }
}
</style>

<template>
  <div class="Events">
    <div class="Events__container">
      <div class="Events__header"
      >
        <img src="~/assets/images/Waves.svg" alt="">
        <h1 class="Events__title">
          Мерориятия
        </h1>
        <img src="~/assets/images/Waves.svg" alt="">
<!--                <div class="Events__video-container" @click="showModal">-->
<!--                    <img src="~/assets/images/Events/Play.svg" alt="">-->
<!--                </div>-->
      </div>

      <div class="Events__slider">
        <div class="Events__slider-navigation">
          <img src="~/assets/images/Events/Slider/navigation/left.svg" @click="prevSlide" alt="left">
          <img src="~/assets/images/Events/Slider/navigation/right.svg" @click="nextSlide" alt="right">
        </div>
        <div class="Events__slider-container">
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
            <Slide v-for="(s ,i) in data" :key="i">
              <div class="Events__slider-block">
                <div class="Events__slider-top" :style="{ 'background-image': `url(${imgAddress(s.img)})` }">
                  <div class="Events__slider-title">
                    <span :style="{ 'background': `${s.tag[1]}` }">{{ s.tag[0] }}</span>
                    <h3>{{ s.title }}</h3>
                  </div>
                  <div class="Events__slider-date">
                    <img src="~/assets/images/Events/calendar.svg" alt="">
                    <span>{{ s.date }}</span>
                  </div>
                </div>
                <div class="Events__slider-bottom">
                  <div class="Events__slider-distance">
                    <div>Дистанции:</div>
                    <span v-for="(d,i) of s.distances" :key="i">{{ d }}</span>
                  </div>
                  <!--                  <div class="Events__slider-date">-->
                  <!--                    <img src="" alt="">-->
                  <!--                    <span>{{ s.date }}</span>-->
                  <!--                  </div>-->
                </div>
              </div>
            </Slide>
          </Carousel>
        </div>
      </div>
      <Modal @hide="show = false" v-if="show"/>
    </div>
  </div>
</template>
<!--                <img :src="require(`~/assets/images/Events/${s}.jpg`)" alt="image"-->
<!--                >-->
<script>
import Modal from "@/components/Modal";
import {Carousel, Slide} from 'vue-carousel'
import Data from '@/assets/content/events'

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
        perPage: 2,
        autoplayTimeout: 10000,
        loop: true,
        direction: 'forward',
        paginationPosition: ['overlay', 'bottom-overlay'],
        speed: 1000,
        paginationEnabled: true,
        paginationColor: '#D1D1D1',
        paginationActiveColor: '#2f70b6'
      },
      data: Data
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
    },
    imgAddress(name) {
      return require(`~/assets/images/Events/${name}.jpg`)
    },

  }
}
</script>


<style scoped lang="scss">
@import "assets/styles/mixins";
@import "assets/styles/variables";

.VueCarousel-wrapper {
  padding: 16px 0 !important;
}
.Events {
  background-color: $white;
  padding: 80px 0;
  @media (max-width: 756px) {
    padding-bottom: 120px;
  }

  &__container {
    @include layout;
    display: flex;
    flex-direction: column;
    grid-gap: unset;
  }

  &__header {
    display: flex;
    justify-content: space-between;

    img {
      width: 240px;
    }
  }

  &__title {
    @include titleH2;
    text-align: center;
  }

  &__slider {
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin-bottom: 24px;

    &-navigation {
      width: 100%;
      display: flex;
      justify-content: space-between;
      position: absolute;
      margin-bottom: 80px;

      img {
        cursor: pointer;
      }
    }

    &-container {
      margin: 0 auto;
      width: 90%;
    }

    &-block {
      @include imageShadow;
      background-color: $white;
      max-width: 440px;
      margin: 16px auto;
      height: 430px;
      border-radius: 6px;
    }

    &-top {
      height: 200px;
      padding: 24px;
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
    }

    &-title {
      span {
        padding: 4px 8px;
        border-radius: 3px;
        font-size: 12px;
        line-height: 12px;
        color: $white;
      }

      h3 {
        margin-top: 12px;
        font-family: Swiyaga, sans-serif;
        line-height: 24px;
        font-size: 18px;
        color: $white;
      }
    }

    &-date {
      color: $white;
      display: flex;
      align-items: center;
      font-size: 12px;
      line-height: 12px;
      img {
        margin-right: 4px;
      }
    }

    &-distance {
      display: flex;
      padding: 16px 24px;
      align-items: center;
      border-bottom: 1px solid #EBEBEB;
      div, span {
        margin-right: 8px;
        font-size: 12px;
        line-height: 12px;
      }
      div {
        font-weight: 700;
      }
      span {
        padding: 4px 8px;
        border: 1px solid $yellow;
        border-radius: 3px;
        color: $black;
        cursor: pointer;
      }
    }
  }

}
</style>

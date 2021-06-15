<template>
  <div class="Events" id="swim">
    <div class="Events__container">
      <div class="Events__header"
      >
        <img src="~/assets/images/Waves.svg" alt="">
        <h2 class="Events__title">
          Мерориятия
        </h2>
        <img src="~/assets/images/Waves.svg" alt="">
      </div>
      <div class="Events__tabs">
        <Tabs
          :tabs-array="tabsArray"
          @SelectedElement="selectElement"
        />
      </div>
      <div class="Events__content">
        <div class="Events__content-block">
          <div class="Events__content-top" :style="{ 'background-image': `url(${imgAddress(selected.img)})` }">
            <div class="Events__content-date">
              <img src="~/assets/images/Events/calendar.svg" alt="">
              <span>{{ selected.date }}</span>
            </div>
            <div class="Events__content-title">
              <span
                :style="{'background': `${selected.tag[1]}`, 'color': `${selected.tag[0] === 'Swimrun' ? '#000000' : '#ffffff'}`}">{{
                  selected.tag[0]
                }}</span>
              <h3>{{ selected.title }}</h3>
            </div>
          </div>
          <div class="Events__content-bottom">
            <div>
              <div class="Events__content-distance">
                <div>Дистанции:</div>
                <span v-for="(d,i) of selected.distances" :key="i">{{ d }}</span>
              </div>
              <div class="Events__content-text">
                <p>{{ selected.description }}</p>
              </div>
            </div>
            <div class="Events__content-buttons">
              <a :href="selected.actionLink" target="_blank" role="button">Зарегистрироваться</a>
              <a :href="selected.moreLink" target="_blank" role="button">Подробнее</a>
            </div>
          </div>
        </div>

      </div>
    </div>
  </div>
</template>


<script>
import distance from "assets/content/distance";
import data from '@/assets/content/events'
import Tabs from "@/components/Tabs";
import Button from "@/components/Button";

export default {
  components: {Button, Tabs},
  data() {
    return {
      selected: data[0]
    }
  },
  computed: {
    tabsArray() {
      return data.map(elem => {
        return {
          title: elem.title,
          id: elem.id
        }
      })
    }
  },
  methods: {
    selectElement(elemID) {
      this.selected = data.find(elem => elem.id === elemID)
    },
    imgAddress(name) {
      return require(`~/assets/images/Events/${name}.jpg`)
    },
  }
}
</script>


<style lang="scss" scoped>
@import "assets/styles/mixins";
@import "assets/styles/variables";

.Events {
  padding: 80px 0;
  background-color: $white;
  @media (max-width: 475px) {
    padding-bottom: 20px;
  }
  &__container {
    @include layout;
  }

  &__header {
    display: flex;
    justify-content: space-between;
    grid-column: 1 / 13;
    margin-bottom: 56px;

    img {
      width: 240px;
    }
    @media (max-width: 756px) {
      flex-direction: column;
      align-items: center;
      margin-bottom: 16px;
      h2 {
        margin: 16px 0;
      }
    }
  }

  &__title {
    @include titleH2;
    text-align: center;
  }

  &__tabs, &__content {
    grid-column: 1/ 13;
  }

  @media (max-width: 756px) {
    &__tabs {
      overflow-x: scroll !important;
      -webkit-overflow-scrolling: touch;
      padding-bottom: 24px;

      &::-webkit-scrollbar {
        -webkit-appearance: none;
      }

      &::-webkit-scrollbar:horizontal {
        height: 12px;
      }

      &::-webkit-scrollbar-thumb {
        background-color: $gray900;
        border-radius: 10px;
        border: 2px solid #ffffff;
      }

      &::-webkit-scrollbar-track {
        border-radius: 10px;
        background-color: $gray300;
      }
    }
  }

  &__content {
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin-bottom: 24px;

    &-block {
      @include imageShadow;
      background-color: $white;
      max-width: 700px;
      margin: 16px auto;
      height: 430px;
      border-radius: 6px;
      display: flex;
      overflow: hidden;
      @media (max-width: 756px) {
        flex-direction: column;
        min-height: 500px;
      }
      @media (max-width: 475px) {
        min-height: 600px;
      }
    }

    &-top {
      padding: 24px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      background-repeat: no-repeat;
      background-position: center;
      background-size: cover;
      width: 40%;
      position: relative;
      z-index: 0;
      height: 100%;
      &::after {
        content: "";
        z-index: -1;
        position: absolute;
        top: 0;
        right: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(180deg, rgba(0, 0, 0, 0) -10.5%, #000000 180.75%);;
      }
      @media (max-width: 756px) {
        width: 100%;
        height: 30%;
        padding: 16px;
      }
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

    &-bottom {
      width: 60%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      @media (max-width: 756px) {
        width: 100%;
        height: 70%;
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
      @media (max-width: 756px) {
        padding: 16px;
      }
    }

    &-text {
      padding: 24px;
      font-size: 12px;
      line-height: 20px;
      color: $black;
      @media (max-width: 756px) {
        padding: 16px;
      }
    }

    &-buttons {
      padding: 24px;
      @media (max-width: 756px) {
        padding: 16px;
      }
      a {
        width: fit-content;
        display: inline-block;
        text-decoration: none;
        border-radius: 6px;
        padding: 10px 16px;
        color: $white;
        background-color: $yellow;
        border: 1px solid $yellow;
        text-decoration: none;
        font-size: 16px;
        line-height: 24px;
        margin-right: 8px;
        -webkit-transition: ease-in-out 0.2s;
        -moz-transition: ease-in-out 0.2s;
        -ms-transition: ease-in-out 0.2s;
        -o-transition: ease-in-out 0.2s;
        transition: ease-in-out 0.2s;
        &:hover {
          background-color: $white;
          border: 1px solid $yellow;
          color: $yellow;
        }
        &:nth-child(2){
          background-color: $white;
          color: $yellow;
          margin-right: unset;
          &:hover {
            background-color: $yellow;
            border: 1px solid $yellow;
            color: $white;
          }
        }
        @media (max-width: 475px) {
          width: 100%;
          text-align: center;
          margin-bottom: 16px;
          &:nth-last-child(1) {
            margin-bottom: unset;
          }
        }
      }
    }
  }

}
</style>

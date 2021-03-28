<template>
  <div class="Location" id="location">

    <iframe
      src="https://yandex.ru/map-widget/v1/?um=constructor%3A094cf5daaea39906da77a64e565893ce9d22187f30aa76685bcc63dbee884558&amp;source=constructor"
      :width="map.width"
      :height="map.height"
      frameborder="0"
      class="Location__map"
    ></iframe>
    <div class="Location__container">
      <h2 class="Location__title">
        Как добраться
      </h2>
      <div class="Location__content">
        <div class="Location__content-tabs">
          <div class="Location__content-element"
               :class="elem.id === activeTab ? 'Location__content-element_active' : null"
               v-for="(elem, i) of tabs"
               :key="i"
               @click="setActive(elem.id)">
            <img :src="require(`~/assets/images/Location/${elem.icon}.svg`)" alt="">
            <p>{{ elem.name }}</p>
          </div>
        </div>
        <div class="Location__content-text">
          <p v-for="(elem, id) of setContent(activeTab)"
             :key="id">
            {{ elem }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      map: {
        width: '100%',
        height: '600'
      },
      activeTab: 1,
      tabs: [{
        id: 1,
        name: 'Автомобиль',
        icon: 'car',
        content: [
          'До остановки «Центральный стадион» на автобусах маршрута 6, 15, 29, 35, 35а, 37, 47, 74, 75',
          'До остановки «Цирк» на автобусах маршрута 22, 28а, 89',
          'До остановки «Дворец спорта» на автобусах маршрута 6, 35а, 37, 47'
        ]
      }, {
        id: 2,
        name: 'Автобус',
        icon: 'bus',
        content: [
          'До остановки «Саид-Галеева» на автобусах маршрута 2, 5, 7, 10а, 30, 53, 63, 72, 74, 91',
          'До остановки «ЦУМ» на автобусах маршрута 5, 6, 35а, 37, 47, 91',
        ]
      }, {
        id: 3,
        name: 'Метро',
        icon: 'metro',
        content: [
          'Лучший способ – доехать на метро до станции «Кремлевская»',
        ]
      }]
    }
  },
  methods: {
    setActive(id) {
      this.activeTab = id
    },
    setContent(id) {
      const data = this.tabs.find(elem => elem.id === id)
      return data.content
    }
  },
}
</script>

<style lang="scss">
@import "assets/styles/mixins";
@import "assets/styles/variables";

.Location {
  position: relative;
  min-height: 700px;
  @media (max-width: 756px) {
    min-height: 900px;
  }
  @media (max-width: 920px) {
    display: flex;
    justify-content: center;
  }
  &__map {
    position: absolute;
    top: 0;
    left: 0;
    z-index: 0;
    @media (max-width: 756px) {
      top: 200px;
    }
  }

  &__container {
    position: absolute;
    width: 480px;
    z-index: 1;
    background-color: $white;
    margin: 56px;
    left: auto;
    @media (max-width: 920px) {
      margin: 0 16px;
      max-width: 756px;
      width: 100%;
      padding: 0 16px;
    ;
    }
  }

  &__title {
    @include titleH2;
    width: 100%;
    text-align: center;
    padding: 16px 0;
    border-bottom: 1px solid #C4C4C4;
  }

  &__content {
    display: flex;
    @media (max-width: 920px) {
      flex-direction: column;
    }
    &-tabs {
      display: flex;
      flex-direction: column;
      @media (max-width: 920px) {
        flex-direction: row;
      }
      @media (max-width: 600px) {
        flex-direction: column;
      }
    }
    &-text {
      padding: 24px;
      p {
        font-size: 16px;
        line-height: 24px;
        margin-bottom: 24px;
        &:nth-last-child(1){
          margin-bottom: 0;
        }
      }
      @media (max-width: 756px) {
        padding: 16px;
      }
    }

    &-element {
      height: 140px;
      width: 140px;
      background-color: $white;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      border-right: 1px solid #C4C4C4;
      border-bottom: 1px solid #C4C4C4;
      -webkit-transition: ease-in-out 0.2s;
      -moz-transition: ease-in-out 0.2s;
      -ms-transition: ease-in-out 0.2s;
      -o-transition: ease-in-out 0.2s;
      transition: ease-in-out 0.2s;
      &:hover {
        background-color: rgba(247, 194, 77, 0.1);
      }
      &:nth-last-child(1) {
        border-bottom: none;
      }
      img {
        margin-bottom: 8px;
        @media (max-width: 756px) {
          width: 40px;
        }
      }
      @media (max-width: 920px) {
        width: 33.3%;
        border: 1px solid #C4C4C4;
        &:nth-last-child(1) {
          border-bottom: 1px solid #C4C4C4;
        }
      }
      @media (max-width: 600px) {
        width: 100%;
        height: 72px;
        flex-direction: row;
        align-items: center;
        justify-content: flex-start;
        padding-left: 16px;
        img {
          margin: 0 16px 0 0;
        }
      }
      &_active {
        background-color: $yellow;

        &:hover {
          background-color: $yellow;
        }

      }

    }
  }
}
</style>

<template>
  <div class="Location" id="location">
    <iframe
      v-if="show"
      src="https://yandex.ru/map-widget/v1/?um=constructor%3A0f65169da2a00b37268a7a0b1485a3dd4cc65d9d8fb2a432f94b35fa2806739e&amp;source=constructor"
      :width="map.width"
      :height="map.height"
      frameborder="0"
      class="Location__map"
    >
    </iframe>
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
      show: false,
      activeTab: 1,
      tabs: [{
        id: 1,
        name: 'Автомобиль',
        icon: 'car',
        content: [
          'Время в пути от центра Казани и вокзала - 1 час 15 минут, из аэропорта Казань - 1 час 40 минут.',
          'Для гостей острова будет действовать бесплатная парковка. Въезд на территорию Свияжска запрещен',
        ]
      }, {
        id: 2,
        name: 'Автобус',
        icon: 'bus',
        content: [
          'Время в пути - 2 часа 40 минут',
          'Отправление от автовокзала “Южный” (пр. Оренбургский, 207)\n',
          'Автобусы отправляются каждую субботу и воскресенье, в праздничные дни.\n' +
          'Время отправления из Казани - 8:40.\n' +
          'Время отправления из Свияжска - 14:30.​​​\n' +
          'Стоимость билета - 150 рублей в одну сторону (льгот нет)​\n',
          'Перед покупкой билетов необходимо узнать подробную информацию о направлении по телефону автовокзала: 8 (843) 2-373-323'
        ]
      }, {
        id: 3,
        name: 'Теплоход',
        icon: 'boat',
        content: [
          'Время в пути - 2 часа 40 минут',
          'Отправление из Речного порта г. Казани (ул. Девятаева, д. 1)',
          'Рейсовые теплоходы ежедневно отправляются:',
          'Отправление из Казани в 9:00.',
          'Отправление из Свияжска в 15:15.',
          'Стоимость билета - 127 рублей в одну сторону. Время в пути - 2-2,5 часа.',
          'Скоростная линия (метеор). Рейс в пятницу, субботу, воскресенье:',
          'Отправление из Казани в 08:30.',
          'Отправление из Свияжска в 12:00.\n' +
          'Стоимость билета туда и обратно - взрослый билет 700 рублей, детский билет 350 рублей. \n',
          'Подробности по тел.: \n' +
          '8 (843) 233-08-08, 8 (843) 233-08-18 (справочная)'
        ]
      }]
    }
  },
  mounted(){
    setTimeout(() => this.show = true, 2000);
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
    border-radius: 6px;
    @include imageShadow;
    overflow: hidden;
    @media (max-width: 920px) {
      margin: 0 16px;
      max-width: 756px;
      width: 100%;
      padding: 0 16px;;
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
      overflow-y: auto;
      max-height: 420px;

      p {
        font-size: 16px;
        line-height: 24px;
        margin-bottom: 24px;

        &:nth-last-child(1) {
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
        color: $white;

        &:hover {
          background-color: $yellow;
        }

      }

    }
  }
}
</style>

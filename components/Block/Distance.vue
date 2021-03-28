<template>
  <div class="Distance" id="distance">
    <h2 class="Distance__title">
      Наши доступные дистанции
    </h2>
    <div class="Distance__container">
      <div class="Distance__tabs">
        <Tabs
          :tabs-array="tabsArray"
          @SelectedElement="selectElement"
        />
      </div>
      <div class="Distance__content">
        <div class="Distance__content-link">
          <a :href="selected.schemeURL">
            <img src="~/assets/images/Distance/File.svg" alt="File">
            Скачать схему дистанции
          </a>
        </div>
        <div class="Distance__content-table">
          <div class="Head">
            <div>Цена</div>
            <div>Доступные слоты</div>
            <div>Участие</div>
          </div>
          <div
            class="Body"
          >
            <div
              class="Body__elem"
              :class="elem.freeSlots === elem.allSlots ? 'Body__elem_disabled' : ''"
              v-for="(elem, i) of selected.slots"
              :key="i"
            >
                <p><span class="mobile">Цена:</span>{{ elem.price + " Рублей" }}</p>
                <p><span class="mobile">Доступные слоты:</span>
                  {{ elem.freeSlots }}<span>/</span>{{ elem.allSlots }}
                </p>
                <a :href="elem.urlTo" :class="elem.freeSlots === elem.allSlots ? 'disabled' : ''">Зарегистрироваться</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import distance from "assets/content/distance";

import Tabs from "@/components/Tabs";

export default {
  components: {Tabs},
  data() {
    return {
      selected: distance[0]
    }
  },
  computed: {
    tabsArray() {
      return distance.map(elem => {
        return {
          distance: elem.distance,
          id: elem.id
        }
      })
    }
  },
  methods: {
    selectElement(elemID) {
      this.selected = distance.find(elem => elem.id === elemID)
    }
  }
}
</script>


<style lang="scss" scoped>
@import "assets/styles/mixins";
@import "assets/styles/variables";

.Distance {
  padding: 80px 0;

  &__container {
    @include layout;
  }

  &__title {
    @include titleH2;
    text-align: center;
    margin-bottom: 56px;
  }

  &__tabs, &__content {
    grid-column: 1/ 13;
  }

  @media (max-width: 756px) {
    &__tabs {
      overflow-x: auto;
    }
  }

  &__content {
    &-link {
      display: flex;
      justify-content: center;
      margin: 24px 0;
      @media (max-width: 756px) {
        margin: 48px 0;
      }

      a {
        display: flex;
        text-decoration: none;
        align-items: center;
        color: $black;
        width: auto;
        font-size: 20px;
        line-height: 20px;

        img {
          margin-right: 16px;
        }
      }
    }

    &-table {
      .Head {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        padding: 18px 0;
        border: 1px solid #F7C24D;
        border-radius: 10px;
        margin-bottom: 32px;

        div {
          text-align: center;
          font-weight: 700;
          font-size: 18px;
          line-height: 18px;
        }

        @media (max-width: 756px) {
          display: none;
        }
      }

      .Body {
        display: flex;
        flex-direction: column;

        &__elem {
          .mobile {
            display: none;
          }
          .disabled {
            background-color: #DCDCDC;
            color: #A7A7A7;
            pointer-events: none;
          }
          &_disabled {
            background-color: #EFEFEF;
          }
          padding: 24px 0;
          display: grid;
          grid-template-columns: repeat(3, 1fr);
          background: $white;
          @include imageShadow;
          box-shadow: 0 2px 2px rgba(0, 0, 0, 0.2);
          margin-bottom: 16px;
          @media (max-width: 756px) {
            display: flex;
            flex-direction: column;
            padding: 32px 0;
            .mobile {
              display: block;
              font-size: 18px;
              line-height: 18px;
              font-weight: 700;
              color: $black;
              margin-bottom: 16px;
            }
            p {
              margin-bottom: 32px;
            }
          }

          p, a {
            text-align: center;
            color: $black;
            align-self: center;
          }

          p {
            font-size: 20px;
            line-height: 20px;

            span {
              margin: 0 8px;
              color: $yellow;
            }
          }

          a {
            padding: 8px 16px;
            background-color: $yellow;
            width: fit-content;
            text-decoration: none;
            font-size: 16px;
            line-height: 24px;
            margin: 0 auto;
          }
        }
      }
    }
  }
}
</style>

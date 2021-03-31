<template>
  <div class="Footer" id="contacts">
    <div class="Footer__container">
      <div class="Footer__logos">
        <img src="~/assets/images/Main/Partners/KM.svg" alt="">
        <a href="https://www.worldmarathonmajors.com/" target="_blank"><img src="~/assets/images/Main/Partners/AWMM.svg" alt=""></a>
        <a href="https://timerman.org/" target="_blank"> <img
          src="~/assets/images/Main/Partners/Timerman.svg"
          alt=""></a>
      </div>
      <div class="Footer__main Footer__structure">
        <h2>Главное</h2>
        <ul>
          <li><a href="#distance">Дистанции</a></li>
          <li><a href="#schedule">Расписание</a></li>
          <li><a href="#timerkids">Timerkids</a></li>
        </ul>
      </div>
      <div class="Footer__info Footer__structure">
        <h2>Информация</h2>
        <ul>
          <li><a href="#location">Как добраться</a></li>
          <li><a href="#legends">Легенды Казани</a></li>
          <li><a href="#FAQ">Вопросы и ответы</a></li>
        </ul>
      </div>
      <div class="Footer__contacts Footer__structure">
        <h2>Контакты</h2>
        <div class="Footer__contacts-data">
          <ul>
            <li><a
              class="Footer__phone"
              href="tel:+79172410144">
              +7 (917) 241-01-44
            </a></li>
            <li>
              <a
                class="Footer__mail"
                href="mailto:corp@timerman.org">
                corp@timerman.org
              </a>
            </li>
          </ul>
          <div class="Footer__social">
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


<style lang="scss" scoped>
@import "assets/styles/mixins";
@import "assets/styles/variables";

.Footer {
  padding: 56px 0;
  border-top: 1px solid #EBEBEB;

  &__container {
    @include layout;
    @media (max-width: 920px) {
      grid-template-columns: 1fr 1fr;
    }
  }

  &__structure {
    li {
      list-style: none;
      margin-bottom: 24px;
      @media (max-width: 480px) {
        margin-bottom: 32px;
      }
    }

    ul {
      margin-top: 32px;
    }

    a {
      text-decoration: none;
      color: $black;
    }

    h2 {
      font-size: 18px;
      line-height: 32px;
      padding-bottom: 8px;
      border-bottom: 3px solid $yellow;
    }
  }

  &__logos {
    grid-column: 1 / 4;
    display: flex;
    flex-direction: column;
    a {
      white-space:nowrap;
    }
    .Timer-logo {
      width: 56px;
    }
    @media (max-width: 920px) {
      grid-column: 1 / 3;
    }
    img {
      width: 120px;
      margin-bottom: 24px;
    }

    @media (max-width: 920px) {
      display: flex;
      flex-direction: row;
      margin-bottom: 32px;
      img {
        width: 120px;
        margin-bottom: 0;
        margin-right: 32px;
        &:nth-last-child(1) {
          margin-right: unset;
        }
      }
    }
    @media (max-width: 480px) {
      justify-content: center;
      flex-direction: column;
      align-items: center;
      img {
        width: 140px;
        margin-right: 0;
        margin-bottom: 24px;
      }
    }
  }

  &__main {
    grid-column: 4 / 7;
    @media (max-width: 920px) {
      grid-column: 1;
    }
    @media (max-width: 480px) {
      grid-column: 1/ 3;
    }
  }

  &__info {
    grid-column: 7 / 10;
    @media (max-width: 920px) {
      grid-column: 2;
    }
    @media (max-width: 480px) {
      grid-column: 1/ 3;
    }
  }

  &__contacts {
    grid-column: 10 / 13;
    @media (max-width: 920px) {
      grid-column: 1 / 3;
    }
    &-data {
      margin-top: 32px;
      a {
        font-size: 20px;
        line-height: 20px;
      }
    }
  }

  &__social {
    display: flex;
    img {
      width: 32px;
      @media (max-width: 480px) {
        width: 56px;
      }
    }
    a {
      margin-right: 8px;
      @media (max-width: 480px) {
        margin-right: 16px;
      }
      &:nth-last-child(1) {
        margin-right: unset;
      }
    }

  }
}
</style>

<template>
  <header class="Header" @mouseleave="resetActive">
    <div class="Header__mobile">
      <div class="Header__logo">
        <router-link to="/">
          <img src="~/assets/images/Header/Timerman.svg" alt="logo">
        </router-link>
      </div>
      <div class="Header__burger" :class="activeMobile && 'Header__burger_active'" @click="openMenu">
        <p>Меню</p>
        <div class="Header__menu">
          <span></span>
          <span></span>
          <span></span>
        </div>
      </div>
    </div>
    <div class="Header__links" :class="activeMobile && 'Header__links_active'">
      <a :href="'#' + link.hash" v-for="(link, i) of links"
         :key="i"
         class="Header__links-elem"
         @click="openMenu"
         @mouseenter="showActive(link.name)">
        <img :src="require(`~/assets/images/Header/Links/${link.hash}.svg`)" alt="">
        <span class="Header__links-elem-text"
              :class="activeLink === link.name ? 'Header__links-elem-text_active' : null">{{ link.name }}</span>
      </a>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      activeMobile: false,
      activeLink: null,
      links: [
        {
          hash: 'main',
          name: 'Главная'
        },
        {
          hash: 'invite',
          name: 'Приглашение'
        },
        {
          hash: 'distance',
          name: 'Дистанции'
        },
        {
          hash: 'schedule',
          name: 'Расписание'
        },
        {
          hash: 'timerkids',
          name: 'Timerkids'
        },
        {
          hash: 'location',
          name: 'Как добраться'
        },
        {
          hash: 'FAQ',
          name: 'Вопрос - Ответ'
        }
      ]
    }
  },
  methods: {
    showActive(name) {
      if (window.innerWidth > 620) {
        this.activeLink = name
      }
    },
    resetActive() {
      this.activeLink = null;
    },
    openMenu() {
      this.activeMobile = !this.activeMobile;
    }
  }
}
</script>


<style scoped lang="scss">
@import "assets/styles/variables";

.Header {
  border-right: 1px solid #EBEBEB;
  height: 100%;
  background-color: $white;
  z-index: 100;
  &__burger {
    display: none;
  }
  @media (max-width: 620px) {
    position: fixed;
    width: 100%;
    height: auto;
    border-right: none;
    &__menu {
      width: 60px;
      display: flex;
      align-items: center;
      height: 100%;
      justify-content: center;
      margin-right: 16px;
      flex-direction: column;
    }
    &__mobile {
      display: flex;
      justify-content: space-between;
      border-bottom: 1px solid #EBEBEB;
    }
    &__burger {
      display: flex;
      height: 80px;
      align-items: center;
      font-size: 14px;
      line-height: 14px;
      text-transform: uppercase;
      cursor: pointer;
      p {
        margin-right: 8px;
      }

      span {
        height: 2px;
        background-color: $black;
        width: 22px;
        position: relative;
        &:nth-child(1), &:nth-last-child(1) {
          height: 2px;
          display: block;
          width: 32px;
          background-color: $black;
          position: relative;
        }

        &:nth-child(1) {
          top: 12px;
        }

        &:nth-last-child(1) {
          bottom: 12px;
        }
      }

      &_active {
        -webkit-transition: ease-in-out 0.2s;
        -moz-transition: ease-in-out 0.2s;
        -ms-transition: ease-in-out 0.2s;
        -o-transition: ease-in-out 0.2s;
        transition: ease-in-out 0.2s;
        span {
          width: 0;
          &:nth-child(1) {
            transform: rotate(45deg);
            top: 0;
          }

          &:nth-last-child(1) {
            transform: rotate(135deg);
            top: -4px;
          }
        }
      }
    }
  }

  &__logo {
    height: 80px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-bottom: 1px solid #EBEBEB;
    @media (max-width: 620px) {
      border-bottom: none;
      width: 80px;
      border-right: 1px solid #EBEBEB;
    }
  }

  &__links {
    display: flex;
    flex-direction: column;
    @media (max-width: 620px) {
      display: none;
      &_active {
        display: flex;
      }
    }

    &-elem {
      height: 80px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-bottom: 1px solid #EBEBEB;
      -webkit-transition: ease-in-out 0.2s;
      -moz-transition: ease-in-out 0.2s;
      -ms-transition: ease-in-out 0.2s;
      -o-transition: ease-in-out 0.2s;
      transition: ease-in-out 0.2s;
      position: relative;
      font-family: MyEurope, serif;
      text-decoration: none;
      color: $black;
      @media (max-width: 620px) {
        justify-content: flex-start;
        padding-left: 16px;
      }

      &:hover {
        background-color: #F5F5F5;
      }

      &-text {
        display: none;
        position: absolute;
        font-size: 14px;
        line-height: 14px;
        z-index: 10;
        @media (max-width: 620px) {
          display: block;
          position: relative;
          font-size: 18px;
          line-height: 18px;
          text-transform: uppercase;
          padding-left: 24px;
        }

        &_active {
          display: block;
          min-width: 150px;
          transform: translateX(135px);
          padding: 8px;
          background-color: #F7C24D;
          border-radius: 2px;
          text-align: center;
        }
      }
    }
  }
}

</style>

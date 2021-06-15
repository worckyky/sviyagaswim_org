<template>
  <div class="Info" id="schedule">
    <div class="Info__container">
      <div class="Info__scheme">
        <h2 class="Info__title">СХЕМА ФЕСТИВАЛЯ</h2>
        <Waves/>
        <p>Здесь вы можете ознакомится со всеми дистациями</p>
        <a href="https://clck.ru/VVHVC" target="_blank">
          <Location/>
          Смотреть схему
        </a>
        <img src="~/assets/images/Info/Tower.svg" alt="">
      </div>
      <div class="Info__schedule">
        <h2 class="Info__title">Расписание</h2>
        <Waves/>
        <a href="" @click.prevent="showModal">
          <Calendar/>
          Смотреть расписание
        </a>
      </div>
    </div>
    <Modal @hide="show = false" v-if="show" title="Расписание">
      <p>Какое-то расписание</p>
      <p>Какое-то расписание</p>
      <p>Какое-то расписание</p>
    </Modal>
  </div>
</template>

<script>
import Location from "@/components/Icons/Location";
import Calendar from "@/components/Icons/Calendar";
import Waves from "@/components/Icons/Waves";
import Modal from "@/components/Modal";

export default {
  components: {Modal, Waves, Calendar, Location},
  data() {
    return {
      show: false
    }
  },
  methods: {
    showModal() {
      this.show = true
    },
  }

}
</script>
<style lang="scss" scoped>
@import "assets/styles/mixins";
@import "assets/styles/variables";

.Info {
  padding: 80px 0;
  @media (max-width: 756px) {
    padding: 20px 0;
  }

  &__container {
    @include layout
  }

  &__title {
    @include titleH2;
    color: $white;
    margin-bottom: 16px;
  }

  &__scheme, &__schedule {
    height: 400px;
    @include imageShadow;
    border-radius: 6px;
    display: flex;
    flex-direction: column;
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    color: $white;
    overflow: hidden;

    &::after {
      content: "";
      z-index: -1;
      position: absolute;
      top: 0;
      right: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.44);
    }

    img {
      width: 240px;
    }

    p {
      margin-top: 40px;
      line-height: 24px;
      font-size: 16px;
    }

    a {
      margin-top: 16px;
      width: fit-content;
      appearance: button;
      display: flex;
      align-items: center;
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

      svg {
        margin-right: 8px;

        path {
          fill: #F7C24D !important;
        }
      }

      &:hover {
        background-color: $white;
        border: 1px solid $yellow;
        color: $yellow;

      }
    }
  }

  &__scheme {
    grid-column: 1 / 8;
    background-image: url("assets/images/Info/map.jpg");
    justify-content: center;
    align-items: flex-start;
    padding: 0 88px;
    position: relative;
    img{
      position: absolute;
      right: 0;
      bottom: 0;
      z-index: -1;
    }
    @media (max-width: 920px) {
      grid-column: 1 / 5;
      padding: 0 40px;
    }
    @media (max-width: 756px) {
      grid-row: 1;
      grid-column: 1 / 9;
      padding: 0 16px;
    }
  }

  &__schedule {
    grid-column: 8 / 13;
    background-image: url("../../assets/images/Info/schedule.jpg");
    justify-content: center;
    align-items: center;

    a {
      margin-top: 40px;
    }

    @media (max-width: 920px) {
      grid-column: 5 / 9;
    }
    @media (max-width: 756px) {
      grid-row: 2;
      grid-column: 1 / 9;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      padding: 0 16px;
    }
  }
}
</style>


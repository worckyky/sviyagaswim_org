<template>
  <div class="Main">
    <div class="Main__container">
      <div class="Main__content">
        <div class="Main__logo">
          <img src="~/assets/images/Main/Partners/Timerman.svg" alt="">
        </div>
        <p class="Main__data">2 мая 2021</p>
        <h1 class="Main__title">
          SVIYAGA <br v-if="checkWidth"> FEST
        </h1>
        <Button>Зарегистрироваться</Button>
      </div>
      <div class="Main__timer">
        <Timer endtime="July 9, 2021 00:00:00"
               starttime="June 12, 2021 00:00:00"
               trans='{
         "day":"Дней",
         "hours":"Часов",
         "minutes":"Минут",
         "seconds":"Seconds",
         "expired":"Event has been expired.",
         "running":"Till the end of event.",
         "upcoming":"Till start of event.",
         "status": {
            "expired":"Expired",
            "running":"Running",
            "upcoming":"Future"
           }}'/>
      </div>
    </div>
  </div>
</template>

<script>
import Button from "@/components/Button";
import Timer from "@/components/Timer";

export default {
  components: {Timer, Button},
  computed: {
    checkWidth() {
      if (window.innerWidth <= 450) {
        return true
      }
    }
  }
}
</script>

<style lang="scss">
@import "assets/styles/variables";
@import "assets/styles/mixins";

.Main {
  background-image: url("assets/images/Main/Bg.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  position: relative;
  height: 600px;
  margin: 24px;
  z-index: 0;
  //@include imageShadow;
  border: 1px solid #EBEBEB;
  border-radius: 6px;
  @media (max-width: 756px) {
    margin: unset;
  }
  @media (max-width: 620px) {
    margin: 80px 0 0 0;
  }
  &::after {
    content: '';
    z-index: -1;
    position: absolute;
    top: 0;
    left: -200px;
    width: 915px;
    height: 601px;
    background: url("assets/images/Main/Vector.png") no-repeat;
    opacity: 0.8;
    @media (max-width: 920px) {
      left: -300px;
    }
    @media (max-width: 475px) {
      left: -600px;
    }
  }

  &__container {
    @include layout;
    @media (max-width: 620px) {
      grid-template-rows: auto auto;
    }
  }

  &__content {
    grid-column: 1 / 8;
    display: flex;
    justify-content: center;
    flex-direction: column;
    @media (max-width: 920px) {
      grid-column: 1 / 10;
    }
    @media (max-width: 756px) {
      grid-row: 1;
      grid-column: 1 / 13;
    }
  }

  &__logo {
    margin-bottom: 80px;
    @media (max-width: 756px) {
      margin: 56px 0;
    }
    img {
      @media (max-width: 756px) {
        width: 180px;
      }
      @media (max-width: 756px) {
        width: 140px;
      }
    }
  }

  &__data {
    text-transform: uppercase;
    font-size: 20px;
    line-height: 20px;
    margin-bottom: 16px;
    @media (max-width: 475px) {
      margin-bottom: 8px;
      font-size: 16px;
    }
  }

  &__title {
    @include titleH1;
    margin-bottom: 48px;
  }
  &__timer {
    display: flex;
    align-items: flex-end;
    grid-column: 12 / 13;
    margin-bottom: 48px;
    position: relative;
    @media (max-width: 920px) {
      justify-content: center;
    }
    @media (max-width: 756px) {
      grid-row: 2;
      justify-content: normal;
      grid-column: 1 / 13;
    }
  }
}

</style>


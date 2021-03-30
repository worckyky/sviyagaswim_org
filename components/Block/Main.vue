<template>
  <div class="Main" id="main">
    <div class="Main__container">
      <div class="Main__content">
        <div class="Main__logo">
          <img src="~/assets/images/Main/Partners/KM.svg" alt="">
          <a href="https://www.worldmarathonmajors.com/" target="_blank"><img src="~/assets/images/Main/Partners/AWMM.svg" alt=""></a>
        </div>
        <p class="Main__data">2 мая 2021</p>
        <h1 class="Main__title">
          Казанский марафон
        </h1>
        <Button>Принять участие!</Button>
      </div>
      <div class="Main__timer">
        <Timer endtime="May 2, 2021 00:00:00"
               starttime="Mar 24, 2021 00:00:00"
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
  components: {Timer, Button}
}
</script>

<style lang="scss">
@import "assets/styles/variables";
@import "assets/styles/mixins";

.Main {
  @media (max-width: 620px) {
    margin-top: 80px;
    height: 640px;
  }
  background-image: url("assets/images/Main/Zilant.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  position: relative;
  height: 600px;
  z-index: 0;

  &::after {
    content: '';
    z-index: -1;
    position: absolute;
    top: 0;
    right: 0;
    width: 100%;
    height: 100%;
    background: radial-gradient(38.86% 100.54% at 73.26% 50.07%,
      rgba(255, 255, 255, 0) 0%,
      rgba(255, 255, 255, 0.51) 57.29%,
      rgba(255, 255, 255, 0.96) 99.6%);
    @media (max-width: 620px) {
      background: radial-gradient(58.14% 51.34% at 100% 50.08%,
        rgba(255, 255, 255, 0) 0%,
        rgba(255, 255, 255, 0.51) 57.29%,
        rgba(255, 255, 255, 0.96) 99.6%);
    }
  }

  &__container {
    @include layout;
    @media (max-width: 620px) {
      grid-template-rows: auto auto;
    }
  }

  &__content {
    grid-column: 1 / 6;
    display: flex;
    justify-content: center;
    flex-direction: column;
    @media (max-width: 920px) {
      grid-column: 1 / 5;
    }
    @media (max-width: 620px) {
      grid-row: 1;
      grid-column: 1 / 1;
    }
  }

  &__logo {
    margin-bottom: 80px;
    @media (max-width: 620px) {
      margin: 56px 0;
    }
    img {
      @media (max-width: 620px) {
        width: 120px;
      }

      &:nth-child(1) {
        margin-right: 16px;
      }
    }
  }

  &__data {
    text-transform: uppercase;
    font-size: 14px;
    line-height: 20px;
  }

  &__title {
    @include titleH1;
    margin-bottom: 48px;
  }
  &__timer {
    display: flex;
    align-items: flex-end;
    grid-column: 7 / 12;
    margin-bottom: 48px;
    @media (max-width: 920px) {
      justify-content: center;
      grid-column: 5 / 9;
    }
    @media (max-width: 620px) {
      grid-row: 2;
      justify-content: normal;
      grid-column: auto;
    }
  }
}

</style>


<template>
  <div class="TimerDragon" id="schedule">
    <div class="TimerDragon__container">
      <div class="TimerDragon__content">
        <h2 class="TimerDragon__title">Расписание</h2>
        <p class="TimerDragon__description">Чтобы ребенок рос здоровым и физически развитым, важно с детства прививать любовь к спорту. </p>
        <a href="/" class="TimerDragon__download">
          <img src="~/assets/images/Timerkids/Kid.svg" alt="">
          Зарегистрировать ребенка
        </a>
      </div>
      <div class="TimerDragon__images">
        <img src="~/assets/images/Timerkids/Timer_dragon.svg" alt="">
      </div>
    </div>
  </div>
</template>


<script>
export default {}
</script>


<style scoped lang="scss">
@import "assets/styles/variables";
@import "assets/styles/mixins";

.TimerDragon {
  margin: 110px 0;
  @media (max-width: 1024px) {
    padding-top: 280px;
    text-align: center;
  }
  @media (max-width: 756px) {
    padding-top: 140px;
  }
  &__container {
    @include layout;
    position: relative;
    align-items: center;
    @media (max-width: 1024px) {
     display: flex;
      justify-content: center;
    }
  }
  &__content {
    display: flex;
    flex-direction: column;
    background-color: #EFEFEF;
    border-radius: 2px;
    grid-column: 1 / 13;
    padding: 56px;
    @media (max-width: 1024px) {
      padding: 56px 32px;
      text-align: center;
      align-items: center;
    }
    @media (max-width: 756px) {
      padding: 56px 0;
      align-items: center;
      width: 100%;
    }

  }
  &__title {
    @include titleH2;
    margin-bottom: 32px;
  }
  &__description {
    font-size: 18px;
    line-height: 28px;
    margin-bottom: 24px;
    max-width: 400px;
    @media (max-width: 1024px) {
      text-align: center;
      max-width: 100%;
      padding: 0 16px;
    }
  }
  &__download {
    display: flex;
    align-items: center;
    width: fit-content;
    text-decoration: none;
    text-align: left;
    color: $black;
    font-size: 20px;
    line-height: 20px;
    img {
      margin-right: 16px;
    }
  }
  &__images {
    position: absolute;
    bottom: 0;
    right: 56px;
    @media (max-width: 1024px) {
      z-index: -1;
      bottom: 270px;
      right: auto;
    }
    @media (max-width: 756px) {
      img {
        width: 320px;
      }
    }
  }
}
</style>

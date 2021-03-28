<template>
  <div class="Schedule" id="schedule">
    <div class="Schedule__container">
      <div class="Schedule__content">
        <h2 class="Schedule__title">Расписание</h2>
        <a href="/" class="Schedule__download">
          <img src="~/assets/images/Schedule/Schedule.svg" alt="">
          Смотреть расписание
        </a>
      </div>
      <div class="Schedule__images">
        <img src="~/assets/images/Schedule/Photos/1.jpg" alt="1">
        <img src="~/assets/images/Schedule/Photos/2.jpg" alt="2">
        <img src="~/assets/images/Schedule/Photos/3.jpg" alt="3">
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

.Schedule {
  padding: 180px 0 120px 0;
  background-color: #fff;
  &__container {
    @include layout;
    position: relative;
    align-items: center;
    @media (max-width: 756px) {
     display: flex;
      justify-content: center;
    }
  }
  &__content {
    display: flex;
    flex-direction: column;
    background-color: #EFEFEF;
    border-radius: 2px;
    grid-column: 1 / 11;
    padding: 100px 0 100px 100px;
    @media (max-width: 1024px) {
      padding: 80px 0 80px 32px;
      grid-column: 1 / 13;
    }
    @media (max-width: 756px) {
      padding: 200px 0 56px 0;
      align-items: center;
      width: 100%;
    }

  }
  &__title {
    @include titleH2;
    margin-bottom: 32px;
  }
  &__download {
    display: flex;
    align-items: center;
    width: fit-content;
    text-decoration: none;
    color: $black;
    font-size: 20px;
    line-height: 20px;
    img {
      margin-right: 16px;
    }
  }
  &__images {
    position: absolute;
    width: 520px;
    height: 420px;
    right: 0;
    margin-right: 16px;
    @media (max-width: 1024px) {
      width: 400px;
      height: 320px;
    }
    @media (max-width: 756px) {
      top: -170px;
      right: auto;
      width: 300px;
      margin: 0;
    }
    img {
      position: absolute;
      @include imageShadow;
      &:nth-child(1) {
        z-index: 3;
        width: 312px;
        right: 32px;
      }
      &:nth-child(2) {
        z-index: 2;
        width: 250px;
        left: 0;
        bottom: 32px;
      }
      &:nth-child(3) {
        z-index: 1;
        width: 380px;
        right: 0;
        bottom: 0;
      }
      @media (max-width: 1024px) {
        &:nth-child(1) {
          width: 240px;
        }
        &:nth-child(2) {
          width: 200px;
          left: 0;
        }
        &:nth-child(3) {
          width: 280px;
        }
      }
    }
  }
}
</style>

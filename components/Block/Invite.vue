<template>
  <div class="Invite" id="invite">
    <span class="Invite__some-text">О мероприятии</span>
    <div class="Invite__container">
      <div class="Invite__images">
        <img src="~/assets/images/Invite/1.jpg" alt="">
        <img src="~/assets/images/Invite/2.jpg" alt="">
        <img src="~/assets/images/Invite/3.jpg" alt="">
      </div>
      <div class="Invite__content">
        <p>Приглашаем на лучшее открытие бегового сезона! </p>
        <p>Казанский марафон - это беговая экскурсия по главным достопримечательностям города с уникальной возможностью
          увидеть столицу в период ее расцвета. </p>
        <p>Приятная весенняя погода, гладкая ровная трасса с небольшим перепадом высот, маршруты в один круг.</p>
        <p>В Казани созданы все условия для того, чтобы ставить личные рекорды.</p>
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

.Invite {
  height: 768px;
  padding: 80px 0;
  position: relative;
  overflow: hidden;

  &__some-text {
    position: absolute;
    z-index: -1;
    font-size: 240px;
    line-height: 300px;
    color: transparent;
    -webkit-text-fill-color: white; /* Will override color (regardless of order) */
    -webkit-text-stroke-width: 1px;
    -webkit-text-stroke-color: $black;
    text-transform: uppercase;
    width: max-content;
    opacity: 0.05;
    font-weight: 700;
  }
  &__container {
    @include layout;
    @media (max-width: 756px) {
      grid-template-rows: repeat(2, 1fr);
    }
  }

  &__images {
    grid-column: 1 / 7;
    position: relative;
    img {
      position: absolute;
      @include imageShadow;

      &:nth-child(1) {
        z-index: 3;
        width: 350px;
        right: 0;
      }

      &:nth-child(2) {
        z-index: 1;
        width: 340px;
        left: 0;
        top: 176px;
      }

      &:nth-child(3) {
        z-index: 1;
        width: 240px;
        right: 32px;
        bottom: 60px;
      }
    }
    @media (max-width: 920px) {
      grid-column: 1 / 5;
      img {
        &:nth-child(1) {
          z-index: 3;
          width: 300px;
          right: 0;
        }

        &:nth-child(2) {
          z-index: 1;
          width: 280px;
          top: 126px;
        }

        &:nth-child(3) {
          z-index: 1;
          width: 200px;
          right: 32px;
          bottom: 140px;
        }
      }
    }
    @media (max-width: 756px) {
      grid-row: 1 ;
      grid-column: 1 / 13;
      height: 300px;
      display: flex;
      justify-content: center;
      img {
        &:nth-child(1) {
          z-index: 3;
          width: 220px;
          right: auto;
          transform: translateX(60px);
          top: -38px;
        }

        &:nth-child(2) {
          z-index: 1;
          width: 240px;
          top: 48px;
          left: auto;
        }

        &:nth-child(3) {
          z-index: 1;
          width: 140px;
          right: auto;
          bottom: 22px;
          transform: translateX(-60px);
        }
      }
    }
  }

  &__content {
    grid-column: 8 / 13;
    display: flex;
    flex-direction: column;
    justify-content: center;
    @media (max-width: 920px) {
      grid-column: 5 / 9;
    }
    @media (max-width: 756px) {
      grid-row: 2 ;
      grid-column: 1 / 13;
      text-align: center;
    }
    p {
      @include paragraph18;
      margin-bottom: 24px;
    }
  }
}
</style>

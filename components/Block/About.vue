<template>
  <div class="About">
    <div class="About__container">
      <div class="About__content">
        <h2>Об острове</h2>
        <img src="~/assets/images/Waves.svg" alt="">
        <p>Свияжск — город-крепость, построенный Иваном Грозным после череды провальных операций по взятию Казани. Было
          необходимо создать опорный пункт для поддержки армии. Крепость возвели всего за 4 недели, а самое главное —
          незаметно для врага.</p>
        <p>Город состоял из восемнадцати башен, жилых домов и православного храма. Крепость полностью выполнила свое
          предназначение: через год после ее основания Казань была взята.</p>
        <p>Сегодня Свияжск — уникальный памятник истории, включенный в список всемирного наследия ЮНЕСКО. Здесь
          гостеприимно встречают туристов со всех уголков нашей страны. Белокаменные монастырские стены, культовые
          православные сооружения и чистый воздух создают невероятную атмосферу спокойствия, величия и нерушимости.</p>
      </div>
      <div class="About__image">
      </div>
      <img class="Tower" src="~/assets/images/About/Tower.svg" alt="">
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "assets/styles/mixins";
@import "assets/styles/variables";

.About {
  padding: 80px 0;
  @media (max-width: 756px) {
    padding-top: unset;
  }
  &__container {
    @include layout;
    display: flex;
    position: relative;
    .Tower {
      position: absolute;
      bottom: 0;
      right: 0;
      z-index: 0;
    }
  }
  &__content {
    width: 700px;
    @include imageShadow;
    padding: 40px;
    background-color: $white;
    display: flex;
    align-items: center;
    flex-direction: column;
    text-align: center;
    border-radius: 6px;
    margin-top: 40px;
    margin-bottom: 80px;
    z-index: 2;
    position: relative;
    @media (max-width: 756px) {
      width: 100%;
      padding: 16px;
      margin-top: 200px;
    }
    h2 {
      @include titleH2;
      margin-bottom: 16px;
    }
    img {
      width: 240px;
      margin-bottom: 40px;
    }
    p {
      margin-bottom: 16px;
      font-size: 16px;
      line-height: 24px;
      @media (max-width: 756px) {
        font-size: 14px;
        line-height: 20px;
      }
    }
  }
  &__image {
    background: url("~/assets/images/About/Bg.jpg") no-repeat center;
    background-size: cover;
    width: 516px;
    height: 404px;
    border-radius: 6px;
    @include imageShadow;
    position: absolute;
    right: 0;
    top: 0;
    z-index: 1;
    @media (max-width: 756px) {
      width: 100%;
    }
  }
}
</style>

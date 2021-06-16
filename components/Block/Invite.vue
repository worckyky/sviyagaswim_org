<template>
  <div class="Invite" id="invite">
    <div class="Invite__container">
      <div class="Invite__content">
        <h2 class="Invite__title">3 дня спортивного праздника <br> на остров-граде Свияжск</h2>
        <img src="~/assets/images/Waves.svg" alt="">
        <p>В программе традиционный заплыв SVIYAGA SWIM, забеги в костюмах и с картами, новый формат SWIMRUN, а еще
          развлекательная программа, детские старты и активности, романтика палаточного городка, невероятная культура
          острова и многое другое!</p>
      </div>
      <div class="Invite__features">
        <div class="Invite__features-elem" v-for="(e, i) of features" :key="i">
          <div class="Invite__features-img">
            <img :src="require(`~/assets/images/Invite/${e.icon}.svg`)" alt="">
          </div>
          <div class="Invite__features-content">
            <h3>{{ e.title }}</h3>
            <p>{{ e.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      features: [
        {
          icon: 'medals',
          title: '4 медальки',
          description: '1 старт - 1 медаль'
        },
        {
          icon: 'shirt',
          title: 'Футболка',
          description: 'Футболка фестиваля при регистрации на все старты'
        },
        {
          icon: 'hands',
          title: 'Ладошки вверх!',
          description: 'Насыщенная программа для каждый день!'
        },
        {
          icon: 'tent',
          title: 'Палатки',
          description: 'Романтика палаточного городка'
        }
      ]
    }
  }
}
</script>


<style scoped lang="scss">
@import "assets/styles/variables";
@import "assets/styles/mixins";

.Invite {
  padding: 100px 0;
  min-height: 600px;
  position: relative;
  overflow: hidden;
  @media (max-width: 475px) {
    min-height: unset;
    height: 1300px;
  }
  &__container {
    @include layout;
    @media (max-width: 756px) {
      grid-template-rows: repeat(2, 1fr);
    }

  }

  &__features {
    grid-column: 6 / 13;
    position: relative;
    display: flex;
    justify-content: flex-end;
    flex-wrap: wrap;
    @media (max-width: 756px) {
      grid-row: 2;
      grid-column: 1 / 13;
    }
    &-img {
      position: absolute;
      background-color: $white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      width: 60px;
      height: 60px;
      @include imageShadow;
      top: -30px;
      left: 16px;
      img {
        width: 32px;
      }
      @media (max-width: 475px) {
        left: unset;
      }
    }
    &-elem {
      flex: 40%;
      min-height: 160px;
      @include imageShadow;
      margin-bottom: 56px;
      background-color: $white;
      border-radius: 6px;
      margin-left: 24px;
      position: relative;
      &:nth-last-child(2n) {
        margin-left: 0;
      }
      @media (max-width: 475px) {
        flex: 100%;
        display: flex;
        margin-left: unset;
        align-items: center;
        justify-content: center;
        height: 146px;
      }
    }
    &-content {
      order: 1;
      padding: 48px 16px 16px 16px;
      height: 100%;
      display: flex;
      flex-direction: column;
      h3 {
        font-family: Swiyaga, Serif;
        font-size: 18px;
        line-height: 24px;
        text-transform: uppercase;
        margin-bottom: 16px;
      }
      p {
        font-size: 14px;
        line-height: 22px;
      }
      @media (max-width: 475px) {
        text-align: center;
      }
    }
  }

  &__title {
    @include titleH2;
    margin-bottom: 16px;
  }

  &__content {
    img {
      width: 240px;
      margin-bottom: 40px;
    }
    grid-column: 1 / 6;
    display: flex;
    flex-direction: column;
    justify-content: center;
    @media (max-width: 920px) {
    }
    @media (max-width: 756px) {
      grid-row: 1;
      grid-column: 1 / 13;
      text-align: center;
      align-items: center;
    }
    p {
      @include paragraph18;
      margin-bottom: 24px;
    }
  }
}
</style>

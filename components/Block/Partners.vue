<template>
  <div class="Partners">
    <div class="Partners__container">
      <h2 class="Partners__title">ПРИ ПОДДЕРЖКЕ</h2>
    </div>
    <div class="Partners__container">
      <div
        class="Partners__block"
        v-for="(brand, i) of partners"
        :key="i"
      >
        <div class="Partners__category">
          <h3>{{ brand.category }}</h3>
        </div>
        <div class="Partners__logos">
          <a class="Partners__elem"
             v-for="(logo, i) of brand.brands"
             :key="i"
             :href="logo[1]"
             target="_blank"
          >
            <img
              :src="require(`~/assets/images/Partners/${logo[0]}`)"
              alt=""
            >
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import partnets from "assets/content/partnets";

export default {
  data() {
    return {
      partners: partnets
    }
  }
}
</script>

<style lang="scss" scoped>
@import "assets/styles/mixins";
@import "assets/styles/variables";

.Partners {
  padding: 80px 0;
  background-color: $white;

  &__container {
    @include layout;
    @media (max-width: 620px) {
      grid-template-columns: 1fr;
    }
  }

  &__title {
    @include titleH2;
    grid-column: 1 / 13;
    margin-bottom: 56px;
    @media (max-width: 620px) {
      grid-column: 1;
      margin-bottom: 32px;
      text-align: center;
    }
  }

  &__block {
    grid-column: 1 / 13;
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    grid-gap: 24px;
    padding: 16px 0;
    border-top: 1px solid #EBEBEB;
    @media (max-width: 620px) {
      grid-column: 1;
      display: flex;
      flex-direction: column;
    }
  }

  &__category {
    grid-column: 1 / 4;
    height: 144px;
    display: flex;
    align-items: center;
    font-size: 16px;
    line-height: 32px;
    @media (max-width: 620px) {
      height: unset;
    }
  }

  &__logos {
    grid-column: 4 / 13;
    display: flex;
    flex-wrap: wrap;
  }

  &__elem {
    display: flex;
    justify-content: center;
    width: 120px;
    height: 120px;
    align-items: center;

    background-color: $white;
    -webkit-transition: ease-in-out 0.2s;
    -moz-transition: ease-in-out 0.2s;
    -ms-transition: ease-in-out 0.2s;
    -o-transition: ease-in-out 0.2s;
    transition: ease-in-out 0.2s;
    margin: 12px;
    @include imageShadow;
    &:hover {
      background-color: rgba(247, 194, 77, 0.1);;
      border: 1px solid $yellow;
    }
    @media (max-width: 620px) {
      margin: 4px;
      flex-basis: 47%;
      flex-shrink: initial;
    }
    img {
      max-width: 80px;
      max-height: 80px;
    }
  }
}
</style>

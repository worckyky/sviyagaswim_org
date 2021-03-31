<template>
  <div class="Questions" id="FAQ">
    <h2 class="Questions__title">Вопросы и ответы</h2>
    <div class="Questions__container">
      <div
        v-for="(q,i) of mapQuestions"
        :key="i"
        class="Questions__element"
      >
        <div
          class="Questions__question"
          @click="setSelected(q.id)"
        >
          <p>{{ q.question }}</p>
          <div class="Questions__open">{{ selected === q.id ? '-' : '+' }}</div>
        </div>
        <div
          :key="i"
          class="Questions__answer"
          :class="selected === q.id ? 'Questions__answer_active' : null"
          ref="Answer"
        >{{ q.answer }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import questions from "assets/content/questions";

export default {
  data() {
    return {
      selected: null
    }
  },
  computed: {
    mapQuestions() {
      return questions.map(q => {
        return {
          id: q.id,
          question: q.question,
          answer: q.answer
        }
      })
    }
  },
  methods: {
    setSelected(id) {
      if (this.$refs.Answer[id - 1].classList.contains('Questions__answer_active')) {
        this.$refs.Answer[id - 1].classList.remove('Questions__answer_active')
        this.selected = null
      } else {
        this.selected = id
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@import "assets/styles/mixins";
@import "assets/styles/variables";

.Questions {
  padding: 80px 0;

  &__container {
    @include layout;
    display: flex;
    flex-wrap: wrap;
    grid-gap: unset;
  }

  &__title {
    @include titleH2;
    text-align: center;
    margin-bottom: 56px;
    @media (max-width: 480px) {
      margin-bottom: 32px;
    }
  }

  &__element {
    margin: 12px;
    height: inherit;
    flex: 40%;
    background-color: $white;
    @include imageShadow;
    @media (max-width: 756px) {
      flex: 100%;
    }
  }

  &__question {
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 24px;
    font-size: 16px;
    line-height: 32px;
    font-weight: 700;
    border-bottom: 1px solid $gray600;
    -webkit-transition: ease-in-out 0.2s;
    -moz-transition: ease-in-out 0.2s;
    -ms-transition: ease-in-out 0.2s;
    -o-transition: ease-in-out 0.2s;
    transition: ease-in-out 0.2s;
    p {
      width: 80%;
    }
    &:hover {
      background-color: rgba(247, 194, 77, 0.1);
    }
    @media (max-width: 756px) {
      padding: 16px;
    }
  }

  &__answer {
    padding: 24px;
    font-size: 18px;
    line-height: 28px;
    display: none;
    @media (max-width: 756px) {
      padding: 16px;
    }

    &_active {
      display: block;
    }
  }

  &__open {
    background-color: $yellow;
    width: 38px;
    height: 38px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: $black;
    border-radius: 50%;
    font-size: 20px;
  }

}
</style>

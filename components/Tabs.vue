<template>
  <div class="Tabs">
    <span
      class="Tabs__element"
      :class="selected === elem.id ? 'Tabs__element_active' : null"
      v-for="(elem, i) of TabsArray"
      :key="i"
      @click="selectTab(elem.id)"
    >
      {{elem.distance}}
    </span>
  </div>
</template>


<script>
export default {
  props: {
    TabsArray: Array[Object]
  },
  data() {
    return {
      selected: this.TabsArray[0].id
    }
  },
  methods: {
    selectTab(tabID) {
      this.selected = tabID
      this.$emit('SelectedElement', tabID)
    }
  }
}
</script>


<style lang="scss" scoped>
@import "assets/styles/mixins";
@import "assets/styles/variables";
.Tabs {
  display: flex;
  justify-content: center;
  @media (max-width: 756px) {
    width: 900px;
  }
  &__element {
    width: 190px;
    display: flex;
    padding: 25px 0;
    border-bottom: 4px solid #C4C4C4;
    justify-content: center;
    cursor: pointer;
    font-size: 20px;
    line-height: 20px;
    -webkit-transition: ease-in-out 0.2s;
    -moz-transition: ease-in-out 0.2s;
    -ms-transition: ease-in-out 0.2s;
    -o-transition: ease-in-out 0.2s;
    transition: ease-in-out 0.2s;
    &_active {
      border-bottom: 4px solid $yellow;
    }
    &:hover {
      background-color: rgba(247, 194, 77, 0.1);;
    }
  }
}
</style>

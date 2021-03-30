<template>
  <div class="Swipe">
    <div class="Swipe__element">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="32"
        height="32"
        fill="none"
        viewBox="0 0 32 32"
      >
        <path
          fill="#212121"
          fill-rule="evenodd"
          d="M25.268 12.3h-.037a1.994 1.994 0 0 0-1.363.545c-.287-.84-1.05-1.442-1.946-1.442a2.015 2.015 0 0 0-1.458.651c-.34-.716-1.04-1.196-1.847-1.196h-.04c-.464 0-.916.139-1.225.414v-5.09C17.352 4.98 16.419 4 15.28 4c-1.137 0-2.067.978-2.067 2.18l-.01 10.067-.61-.743a2.828 2.828 0 0 0-1.998-1.049 2.784 2.784 0 0 0-2.084.738l-.492.408a.412.412 0 0 0-.103.507l4.785 9.187c.87 1.672 2.526 2.705 4.322 2.705h5.367c2.721 0 4.938-2.352 4.94-5.252l.003-2.032v-1.012c.004-2.113.005-2.903 0-5.229-.004-1.2-.93-2.175-2.065-2.175zm1.242 7.407l-.001 1.005v.005l-.002 2.03c-.003 2.446-1.85 4.43-4.117 4.43h-5.367c-1.487 0-2.863-.863-3.591-2.262L8.8 16.02l.244-.2.006-.006a1.965 1.965 0 0 1 1.487-.538c.556.043 1.07.315 1.419.751l1.338 1.63a.412.412 0 0 0 .73-.26l.009-11.216c0-.748.564-1.357 1.248-1.357.683 0 1.247.61 1.247 1.358v6.798a1.37 1.37 0 0 0 0 .05v2.907a.412.412 0 0 0 .824 0V12.96c0-.723.56-1.277 1.226-1.277h.039c.684 0 1.257.585 1.257 1.334v2.645a.412.412 0 0 0 .824 0v-2.075c0-.75.55-1.359 1.237-1.359.684 0 1.234.61 1.234 1.359v1.958a.412.412 0 0 0 .823 0v-1.06c0-.75.555-1.36 1.24-1.36h.036c.682 0 1.239.608 1.24 1.355.006 2.324.005 3.115.002 5.228zM18.793 8.079h5.337l-.957.957a.412.412 0 1 0 .583.582l1.654-1.654a.412.412 0 0 0 0-.582l-1.654-1.654a.412.412 0 0 0-.583.583l.945.944h-5.325a.412.412 0 1 0 0 .824zm-7.103 0H6.4l.957.957a.412.412 0 1 1-.583.582L5.12 7.964a.412.412 0 0 1 0-.582l1.654-1.654a.412.412 0 0 1 .583.583l-.945.944h5.278a.412.412 0 0 1 0 .824z"
          clip-rule="evenodd"
        />
      </svg>
    </div>
    <div class="Tabs">
    <span
      class="Tabs__element"
      :class="selected === elem.id ? 'Tabs__element_active' : null"
      v-for="(elem, i) of TabsArray"
      :key="i"
      @click="selectTab(elem.id)"
    >
      {{ elem.distance }}
    </span>
    </div>
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


.Swipe {
  position: relative;

  &__element {
    display: none;
    @media (max-width: 756px) {
      display: block;
      animation: yourAnimation 1.4s infinite ease-in-out;
      margin-bottom: 16px;
      width: fit-content;
      position: absolute;
      right: 0;
    }
  }
}

@keyframes yourAnimation {
  0% {
    transform: translateX(0px);
    opacity: 1;
  }

  50% {
    transform: translateX(-40px);
    opacity: 0;
  }

  100% {
    transform: translateX(0px);
    opacity: 0;
  }
}

.Tabs {
  display: flex;
  justify-content: center;
  @media (max-width: 756px) {
    width: 1000px;
    padding-top: 56px;
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

    @media (max-width: 756px) {
      @include imageShadow;
      background-color: #fff;
      border-radius: 6px;
      margin: 0 4px;
      padding: 48px 25px;
    }
  }
}
</style>

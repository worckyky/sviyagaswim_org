<template>
  <div class="Timer">
    <div class="Timer__title">
      До старта
    </div>
    <div class="Timer__content">
      <div class="Timer__content-elem day">
        <span class="Timer__content-number">{{ days }}</span>
        <div class="Timer__content-format">{{ wordString.day }}</div>
      </div>
      <div class="Timer__content-elem hour">
        <span class="Timer__content-number">{{ hours }}</span>
        <div class="Timer__content-format">{{ wordString.hours }}</div>
      </div>
      <div class="Timer__content-elem minute">
        <span class="Timer__content-number">{{ minutes }}</span>
        <div class="Timer__content-format">{{ wordString.minutes }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['starttime', 'endtime', 'trans'],
  data: function () {
    return {
      timer: "",
      wordString: {},
      start: "",
      end: "",
      interval: "",
      days: "",
      minutes: "",
      hours: "",
      seconds: "",
      message: "",
      statusType: "",
      statusText: "",
    };
  },
  created: function () {
    this.wordString = JSON.parse(this.trans);
  },
  mounted() {
    this.start = new Date(this.starttime).getTime();
    this.end = new Date(this.endtime).getTime();
    // Update the count down every 1 second
    this.timerCount(this.start, this.end);
    this.interval = setInterval(() => {
      this.timerCount(this.start, this.end);
    }, 1000);
  },
  methods: {
    timerCount: function (start, end) {
      // Get todays date and time
      let now = new Date().getTime();

      // Find the distance between now an the count down date
      let distance = start - now;
      let passTime = end - now;

      if(distance < 0 && passTime < 0){
        this.message = this.wordString.expired;
        this.statusType = "expired";
        this.statusText = this.wordString.status.expired;
        clearInterval(this.interval);
        return;

      }else if(distance < 0 && passTime > 0){
        this.calcTime(passTime);
        this.message = this.wordString.running;
        this.statusType = "running";
        this.statusText = this.wordString.status.running;

      } else if( distance > 0 && passTime > 0 ){
        this.calcTime(distance);
        this.message = this.wordString.upcoming;
        this.statusType = "upcoming";
        this.statusText = this.wordString.status.upcoming;
      }
    },
    calcTime: function (dist) {
      // Time calculations for days, hours, minutes and seconds
      this.days = Math.floor(dist / (1000 * 60 * 60 * 24));
      this.hours = Math.floor((dist % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      this.minutes = Math.floor((dist % (1000 * 60 * 60)) / (1000 * 60));
      this.seconds = Math.floor((dist % (1000 * 60)) / 1000);
    }

  }
}
</script>


<style scoped lang="scss">
  @import "assets/styles/variables";
  .Timer {
    display: flex;
    flex-direction: column;
    position: absolute;
    z-index: 2;
    align-items: center;
    bottom: -100px;
    right: 0;
    @media (max-width: 756px) {
      width: 100%;
    }
    &__title {
      position: absolute;
      z-index: 1;
      top: -30px;
      font-size: 50px;
      line-height: 50px;
      text-align: center;
      width: auto;
      margin-bottom: 16px;
      display: flex;
      align-items: center;
      overflow: hidden;
      font-weight: 700;
      text-transform: uppercase;
      color: transparent;
      -webkit-text-fill-color: transparent; /* Will override color (regardless of order) */
      -webkit-text-stroke-width: 1px;
      -webkit-text-stroke-color: $white;
      border-image-source: linear-gradient(180deg, #FBFBFB 45.68%, rgba(251, 251, 251, 0) 100%);
      @media (max-width: 756px) {
        -webkit-text-stroke-color: $black;
      }
      @media (max-width: 475px) {
        -webkit-text-stroke-color: $white;
      }

    }
    &__content {
      display: flex;
      //justify-content: space-between;
      &-elem {
        //box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.2);
        border: 1px solid #EBEBEB;
        margin-right: 24px;
        z-index: 3;
        width: 120px;
        border-radius: 6px;
        @media (max-width: 756px) {
          width: 100px;
          margin-right: 8px;
        }
        &:nth-last-child(1) {
          margin-right: 0;
        }
      }
      &-number, &-format {
        background-color: $white;
        display: flex;
        align-items: center;
        justify-content: center;
      }

      &-number {
        border-radius: 6px 6px 0 0;
        font-size: 32px;
        line-height: 32px;
        height: 64px;
        border-bottom: 1px solid $gray300;
      }
      &-format {
        border-radius: 0 0 6px 6px;
        font-size: 14px;
        line-height: 14px;
        height: 36px;
      }
    }
  }
</style>

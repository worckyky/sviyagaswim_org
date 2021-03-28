<template>
  <div class="Timer">
    <div class="Timer__title">
      До начала мероприятия:
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
    width: 260px;
    &__title {
      font-size: 14px;
      line-height: 14px;
      padding: 9px 16px;
      width: auto;
      margin-bottom: 16px;
      background-color: $white;
      position: relative;
      display: flex;
      align-items: center;
      overflow: hidden;
      &::after {
        position: absolute;
        content: '';
        right: 0;
        background: url("../assets/images/Main/Element.svg") no-repeat center;
        background-size: cover;
        width: 60px;
        height: 32px;
      }
    }
    &__content {
      display: flex;
      justify-content: space-between;
      &-number, &-format {
        background-color: $white;
        width: 76px;
        display: flex;
        align-items: center;
        justify-content: center;
      }
      &-number {
        font-size: 32px;
        line-height: 32px;
        height: 64px;
        margin-bottom: 16px;
      }
      &-format {
        font-size: 14px;
        line-height: 14px;
        height: 36px;
      }
    }
  }
</style>

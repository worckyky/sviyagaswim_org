<template>
  <div class="Scroll">
    <Main/>
    <Invite/>
    <LastYear/>
    <Distance/>
    <Schedule/>
    <Timerkids/>
    <TimerDragon/>
    <Location/>
    <Expo/>
    <Legends/>
    <Reserch/>
    <Social/>
    <Questions/>
    <Partners/>
    <Footer/>
  </div>
</template>

<script>
import Main from "~/components/Block/Main";
import Invite from "@/components/Block/Invite";
import LastYear from "@/components/Block/LastYear";
import Distance from "@/components/Block/Distance";
import Schedule from "@/components/Block/Schedule";
import Timerkids from "@/components/Block/Timerkids";
import TimerDragon from "@/components/Block/TimerDragon";
import Location from "@/components/Block/Location";
import Expo from "@/components/Block/Expo";
import Legends from "@/components/Block/Legends";
import Reserch from "@/components/Block/Reserch";
import Social from "@/components/Block/Social";
import Questions from "@/components/Block/Questions";
import Partners from "@/components/Block/Partners";
import Footer from "@/components/Block/Footer";

export default {
  components: {
    Footer,
    Partners,
    Social,
    Reserch, Expo, Location, TimerDragon, Timerkids, Schedule, Distance, LastYear, Invite, Main, Legends, Questions}
}
</script>

<style lang="scss">
  .Scroll {
    overflow-y: Scroll;
    overflow-x: hidden;
  }
</style>

<template>
  <div class="Scroll">
    <Main/>
    <Invite/>
<!--    <Events/>-->
    <Distance/>
    <Info/>
    <Live/>
<!--    <Schedule/>-->
<!--    <TimerDragon/>-->
    <Location/>
    <About/>
<!--    <Expo/>-->
    <Legends/>
<!--    <Reserch/>-->
    <Social/>
    <Questions/>
    <Partners/>
    <Footer/>
  </div>
</template>

<script>
import Main from "~/components/Block/Main";
import Invite from "@/components/Block/Invite";
import Events from "@/components/Block/Events";
import Distance from "@/components/Block/Distance";
import Schedule from "@/components/Block/Schedule";
import TimerDragon from "@/components/Block/TimerDragon";
import Location from "@/components/Block/Location";
import Expo from "@/components/Block/Expo";
import Legends from "@/components/Block/Legends";
import Reserch from "@/components/Block/Reserch";
import Social from "@/components/Block/Social";
import Questions from "@/components/Block/Questions";
import Partners from "@/components/Block/Partners";
import Footer from "@/components/Block/Footer";
import Info from "@/components/Block/Info";
import Live from "@/components/Block/Live";
import About from "@/components/Block/About";

export default {
  components: {
    About,
    Live,
    Info,
    Footer,
    Partners,
    Social,
    Reserch, Expo, Location, TimerDragon, Schedule, Distance, Events, Invite, Main, Legends, Questions}
}
</script>

<style lang="scss">
  .Scroll {
    overflow-y: Scroll;
    overflow-x: hidden;
  }
</style>

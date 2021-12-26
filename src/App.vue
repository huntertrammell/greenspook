
<template>
  <Controls />
  <Intro />
</template>

<style lang="scss">
body {
  font-family: "Montserrat", sans-serif;
  background-image: url("assets/images/bkg/wallColor.png");
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  margin: 0;
}

// MOBILE
.mobile-stack {
  &_item {
    &--top {
      @media (max-width: $lg) {
        z-index: 20;
      }
    }
    @media (max-width: $lg) {
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
    }
  }

  @media (max-width: $lg) {
    position: relative;
    overflow: hidden;
    height: 100vh;
    width: 100vw;
    z-index: 5;
    margin: 0 !important;
  }
}
</style>

<script>
import { gsap } from "gsap";
import Intro from "./pages/Intro.vue";
import Controls from "./components/controls.vue";
export default {
  mounted() {
    const title = this.$refs.title;
    gsap.from(title, { duration: 1, scale: 1.5, x: 300 });
  },
  components: {
    Intro,
    Controls,
  },
};
</script>

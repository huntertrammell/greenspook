
<template>
  <Intro />
</template>

<style>
body {
  background-image: url("./assets/images/bkg/wallColor.png");
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  margin: 0;
}
</style>

<script>
import { gsap } from "gsap";
import Intro from "./pages/Intro.vue";
export default {
  mounted() {
    const title = this.$refs.title;
    gsap.from(title, { duration: 1, scale: 1.5, x: 300 });
  },
  components: {
    Intro,
  },
};
</script>


<template>
  <h1 ref="title">Hello World</h1>
</template>

<style>
</style>

<script>
import { gsap } from "gsap";
export default {
  mounted() {
    const title = this.$refs.title;
    gsap.from(title, { duration: 1, scale: 1.5, x: 300 });
  },
};
</script>

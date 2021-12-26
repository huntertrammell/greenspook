<template>
  <div @mouseenter="lightingEfx" class="frame-item" :id="id">
    <slot />
    <audio ref="audio" :src="currentSrc" />
  </div>
</template>

<script>
import { gsap } from "gsap";
export default {
  data() {
    return {
      name: "lighting",
      audioSrc: ["/assets/audio/lighting_audio/lighting_one.mp3"],
      currentSrc: "",
      isAnimationActive: false,
      id: "",
    };
  },
  props: {
    gsapSelector: String,
  },
  computed: {
    animated() {
      return `${this.gsapSelector}_${this.getInterval(99999, 10000)}`;
    },
  },
  methods: {
    lightingEfx() {
      // lighting Animation
      if (!this.isAnimationActive) {
        this.isAnimationActive = !this.isAnimationActive;
        this.$refs.audio.play();
        gsap.set(`#${this.id} .frame-item_clip-path`, {
          opacity: 1,
        });
        gsap.to(
          `#${this.id} .gs-lighting_person, #${this.id} .frame-item_clip-path`,
          {
            opacity: 0,
            duration: 0.5,
          }
        );
        setTimeout(() => {
          gsap.to(`#${this.id} .gs-lighting_person`, {
            opacity: 1,
            duration: 0.5,
          });
          this.isAnimationActive = !this.isAnimationActive;
        }, this.getInterval(15000, 5000));
      }

      let self = this;
      this.$refs.audio.onended = function () {
        self.currentSrc = self.randomItem(self.audioSrc);
      };
    },
    randomItem(array) {
      let index = Math.floor(Math.random() * array.length);
      return array[index];
    },
    getInterval(max, min) {
      return Math.floor(Math.random() * (max - min) + min);
    },
  },
  mounted() {
    this.currentSrc = this.randomItem(this.audioSrc);
    this.id = this.animated;
  },
};
</script>


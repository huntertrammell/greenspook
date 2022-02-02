<template>
  <div @mouseenter="lightingEfx" class="frame-item" :id="id">
    <slot />
    <audio ref="audio" :src="currentSrc" />
  </div>
</template>

<style lang="scss">
/* Frame */
.frame {
  width: 100%;
  height: 100vh;
  &-item {
    position: relative;
    width: 275px;
    height: auto;
    @media (max-width: $md) {
      width: 225px;
    }
    &:nth-child(1) {
      left: 2%;
      top: 2%;
      @media (max-width: $sm) {
        left: -10%;
        top: -10%;
      }
    }
    &:nth-child(2) {
      top: 68%;
      left: 5%;
      @media (max-width: $sm) {
        left: 68%;
        top: 39%;
      }
    }
    &:nth-child(3) {
      top: 40%;
      left: 50%;
      @media (max-width: $lg) {
        left: 68%;
        top: 58%;
      }
      @media (max-width: $md) {
        top: 65%;
      }
      @media (max-width: $sm) {
        right: unset;
        bottom: 2%;
        left: 5%;
      }
    }
    &_clip-path {
      background-color: rgb(235, 235, 235);
      position: absolute;
      display: block;
      opacity: 0;
      &--couple {
        clip-path: ellipse(50% 50% at 50% 50%);
        width: 275px;
        height: 399px;
        @media (max-width: $md) {
          width: 225px;
          height: 327px;
        }
      }
      &--fisher {
        clip-path: polygon(0 0, 100% 0%, 100% 100%, 0% 100%);
        width: 275px;
        height: 236px;
        @media (max-width: $md) {
          width: 225px;
          height: 193px;
        }
      }
      &--family {
        clip-path: polygon(
          25% 0%,
          75% 0%,
          100% 50%,
          75% 100%,
          25% 100%,
          0% 50%
        );
        width: 275px;
        height: 239px;
        @media (max-width: $md) {
          width: 225px;
          height: 196px;
        }
      }
    }
    img {
      position: absolute;
      display: block;
      width: 100%;
      height: auto;
    }
  }
}
</style>

<script>
import { gsap } from "gsap";
export default {
  data() {
    return {
      name: "lighting",
      audioSrc: [
        "/assets/audio/lighting_audio/lighting_one.mp3",
        "/assets/audio/lighting_audio/lighting_two.mp3",
        "/assets/audio/lighting_audio/NEW_Lightning_1.wav",
        "/assets/audio/lighting_audio/NEW_Lightning_2.wav",
        "/assets/audio/lighting_audio/NEW_Lightning_3.mp3",
      ],
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


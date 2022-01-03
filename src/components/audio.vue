<template>
  <div class="control">
    <audio
      :src="audio.src"
      :autoplay="audio.autoplay"
      :loop="audio.loop"
      :aria-controls="_id"
      ref="audio"
    ></audio>
    <button
      class="control_toggler"
      @click="toggleState"
      :id="_id"
      :key="playing"
    >
      <img
        class="control_toggler-icon"
        :src="imgSrc"
        :alt="button.alt"
        height="30"
        width="30"
      />
    </button>
  </div>
</template>
<style lang="scss">
.control {
  margin: 0 0.25rem;
  &_toggler {
    border-radius: 50%;
    padding: 0.5rem;
    background-color: #303030;
    &-icon {
      color: $primary-font;
    }
  }
}
</style>
<script>
export default {
  props: {
    button: Object,
    audio: Object,
    _id: String,
  },
  data() {
    return {
      playing: false,
      currentSrc: "",
    };
  },
  computed: {
    audioState() {
      if (this.playing) {
        return "on";
      } else {
        return "off";
      }
    },
    imgSrc() {
      return this.button.src + this.audioState + this.button.type;
    },
  },
  methods: {
    toggleState() {
      this.playing = !this.playing;
    },
  },
  watch: {
    playing(newValue, oldValue) {
      let music = this.$refs.audio;
      let tracks = document.querySelectorAll("audio");
      if (music.paused) {
        tracks.forEach((track) => {
          track.muted = !track.muted;
        });
        console.log(this.$refs);
        music.play();
      } else {
        tracks.forEach((track) => {
          track.muted = !track.muted;
        });
      }
    },
  },
  mounted() {
    let tracks = document.querySelectorAll("audio");
    tracks.forEach((track) => {
      track.muted = true;
    });
  },
};
</script>

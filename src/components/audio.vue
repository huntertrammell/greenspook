<template>
  <div class="control">
    <audio
      :src="audio.random ? currentSrc : audio.src"
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
    randomItem(array) {
      let index = Math.floor(Math.random() * array.length);
      return array[index];
    },
    getInterval(max, min) {
      return Math.floor(Math.random() * (max - min) + min);
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
      if (this.audio.random) {
        function play() {
          let interval = this.getInterval(30000, 7000);
          let timer = setTimeout(() => {
            music.play();
          }, interval);
        }
        function stop() {
          clearTimeout(timer);
        }
        if (newValue) {
          /* 
          pick a random audio file,
          set random inteval,
          when interval is recieved we need to play audio,
          when audio completes pick new audio and interval
          */
          this.currentSrc = this.randomItem(this.audio.src);
          play();
        } else {
          /*
          if toggle is set to off we neeed to pause audio
          clear inteval
          */
          stop();
        }
      } else {
        if (music.paused) {
          console.log("Playing Audio");
          music.play();
        } else {
          music.muted = !music.muted;
        }
      }
    },
  },
  // mounted() {

  // },
};
</script>

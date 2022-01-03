<template>
  <div class="controls">
    <p>Toggle Audio</p>
    <Ctrl
      v-for="(btn, index) in buttons"
      :key="'btn_' + index"
      :button="btn.button"
      :audio="btn.audio"
      :_id="btn.name + '_' + index"
    />
  </div>
</template>
<style lang="scss">
.controls {
  display: flex;
  position: fixed;
  justify-content: center;
  align-items: center;
  z-index: 50;
  top: 2%;
  right: 2%;
  border-radius: 50px;
  padding: 0.5rem;
  background-color: #303030;
  p {
    color: #f8f8f8f8;
    margin-bottom: 0;
    padding: 0rem 0.5rem 0rem 1rem;
    font-weight: 600;
  }
}
</style>

<script>
import Ctrl from "./audio.vue";
export default {
  data() {
    return {
      buttons: [
        {
          name: "main_track",
          audio: {
            src: "/assets/audio/main_audio/main_track.wav",
            autoplay: false,
            loop: true,
            random: false,
          },
          button: {
            src: "/assets/images/utils/audio_",
            alt: "audio control icon",
            type: ".svg",
          },
        },
      ],
    };
  },
  components: {
    Ctrl,
  },
};
</script>

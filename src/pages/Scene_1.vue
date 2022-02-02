<template>
  <section class="section-scene-1" role="contentinfo" aria-label="scene 1">
    <div class="scene-1__main-focus">
      <img
        class="scene-1__trees scene-1__layers"
        src="/assets/images/scene_1/Trees_Ground.png"
        alt="Trees and Ground"
        width="1920"
        height="1123"
      />
      <img
        class="scene-1__trees scene-1__layers"
        src="/assets/images/scene_1/Church_Grave_Bg.png"
        alt="Trees and Ground"
        width="1920"
        height="1123"
      />
      <div class="scene-1__layers scene-1__graves"></div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.section-scene-1 {
  background-image: url(/assets/images/scene_1/Sky.png);
}
.scene-1 {
  &__main-focus {
    position: relative;
    overflow: hidden;
    width: 100%;
    height: 1920px;
  }
  &__layers {
    position: absolute;
    top: 0;
    width: 100vw;
    height: auto;
  }
  &__graves {
    background-image: url(/assets/images/scene_1/GRAVES_FOREGROUND.png);
    background-repeat: no-repeat;
    bottom: 0 !important;
  }
}
</style>
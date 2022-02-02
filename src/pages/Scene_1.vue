<template>
  <section class="section-scene-1" role="contentinfo" aria-label="scene 1">
    <div class="scene-1__story">
      <img
        class="scene-1__story--moon"
        src="/assets/images/scene_1/Creature.png"
        alt="moon"
        width="312"
        height="467"
      />
      <div class="scene-1__story--text">
        <p>Cold winter night - bright stars like teeth</p>
        <p>Shed light on churchyard underneath</p>
        <p>Graves like eyes, covered with snow</p>
        <p>Shine under the moon’s gray glow</p>
      </div>
    </div>
    <div class="scene-1__main-focus">
      <img
        class="scene-1__trees scene-1__layers"
        src="/assets/images/scene_1/Trees_Ground.png"
        alt="Trees and Ground"
        width="1920"
        height="1123"
      />
      <img
        class="scene-1__church scene-1__layers"
        src="/assets/images/scene_1/Church_Grave_Bg.png"
        alt="Church and Ground"
        width="1920"
        height="1123"
      />
      <img
        class="scene-1__graves scene-1__layers"
        src="/assets/images/scene_1/GRAVES_FOREGROUND.png"
        alt="Graves"
        width="1920"
        height="1123"
      />
    </div>
  </section>
</template>

<style lang="scss" scoped>
.section-scene-1 {
  background-image: url(/assets/images/scene_1/Sky.png);
}
.scene-1 {
  &__story {
    display: flex;
    justify-content: space-between;
    align-items: center;
    &--moon {
      padding-top: 5rem;
      padding-left: 6rem;
    }
    &--text {
      padding-top: 6rem;
      padding-right: 4rem;
      font-size: 2.5rem;
      color: white;
      font-weight: 600;
    }
  }
  &__main-focus {
    position: relative;
    overflow: hidden;
    width: 100%;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: center;
  }
  &__layers {
    position: absolute;
    width: 100%;
    height: auto;
    object-fit: cover;
  }
  &__graves {
  }
}
</style>
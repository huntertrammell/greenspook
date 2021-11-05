<template>
  <section role="contentinfo" aria-label="Poem introduction">
    <div class="container-fluid p-0">
      <!-- Row -->
      <div class="mobile-stack row">
        <!-- column -->
        <div
          class="mobile-stack_item mobile-stack_item--top col-md-12 col-lg-6"
        >
          <!-- INTRO TEXT -->
          <div class="intro-menu">
            <div class="p-1 text-center">
              <h1>ColD<br />WinteR<br />NighT</h1>
              <nav>
                <ul>
                  <li>TexT 1</li>
                  <li>TexT 2</li>
                  <li>TexT 3</li>
                  <li>TexT 4</li>
                </ul>
              </nav>
            </div>
          </div>
        </div>
        <!-- column -->
        <div class="mobile-stack_item col-md-12 col-lg-6">
          <!-- Position Relative -->
          <div class="frame">
            <!-- Couple Frame Position Absolute-->
            <div class="frame-item">
              <!-- Position Relative -->

              <img
                src="/assets/images/intro/couple/BACKGROUND_For_COUPLE.png"
                alt="picture frame background"
                width="460"
                height="669"
              />
              <!-- Guy_Couple -->
              <img
                src="/assets/images/intro/couple/Guy_Couple_Only.png"
                alt="guy in couple picture"
                width="460"
                height="669"
              />
              <!-- Girl Couple -->
              <img
                src="/assets/images/intro/couple/Women_COUPLE_Only.png"
                alt="Women in couple picture"
                width="460"
                height="669"
              />
              <!-- Couple Frame -->
              <img
                src="/assets/images/intro/couple/FRAME_For_COUPLE.png"
                alt="Frame for couple picture"
                width="460"
                height="669"
              />
            </div>

            <!-- Fisherman Frame -->
            <div class="frame-item">
              <img
                src="/assets/images/intro/FrameFishing.png"
                alt="couple in picture"
                width="622"
                height="536"
              />
            </div>
            <!-- Family Frame -->
            <div class="frame-item">
              <img
                src="/assets/images/intro/FrameFamily.png"
                alt="couple in picture"
                width="679"
                height="592"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@include font('BlackLagoon', '@/assets/fonts/blackLagoon/BlackLagoon');
.intro-menu {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  background: radial-gradient(
    ellipse,
    rgba(0, 0, 0, 0.75) 30%,
    rgba(0, 0, 0, 0) 75%
  );
  h1 {
    font-family: 'BlackLagoon';
    color: $primary-font;
    font-size: 5rem;
    line-height: 0.76;
    letter-spacing: 0.2rem;
  }
  nav {
    ul {
      list-style-type: none;
      display: flex;
      flex-direction: column;
      text-align: center;
      align-items: center;
      justify-content: center;
      padding: 0;
      margin: 0;
      li {
        color: $primary-font;
        font-size: 2rem;
        font-weight: 600;
      }
    }
    @media (max-width: $lg) {
      display: none;
    }
  }
}

/* Scene Wrapper */
section {
  height: 100vh;
  width: 100vw;
  background-image: url('../assets/images/bkg/bricks.png');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
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
    img {
      position: absolute;
      display: block;
      width: 100%;
      height: auto;
    }
  }
}
</style>

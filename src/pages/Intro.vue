<template>
  <section role="contentinfo" aria-label="Poem introduction">
    <div class="container-fluid">
      <div class="row">
        <div class="col-md-12 col-lg-6">
          <h1>TITLE OF POEM</h1>
          <p>
            Lorem ipsum dolor sit amet consectetur, adipisicing elit. Atque,
            laudantium. Omnis consectetur unde repellat, distinctio aut beatae
            facilis atque eos velit consequuntur doloremque sunt praesentium
            nisi modi voluptatibus incidunt eius.
          </p>
        </div>
        <div class="col-md-12 col-lg-6">
          <div class="frame">
            <!-- Couple Frame -->
            <div class="frame-item">
              <img
                src="../assets/images/intro/FrameeCouple.png"
                alt="couple in picture"
                width="460"
                height="669"
              />
            </div>
            <!-- Fisherman Frame -->
            <div class="frame-item">
              <img
                src="../assets/images/intro/FrameFishing.png"
                alt="couple in picture"
                width="622"
                height="536"
              />
            </div>
            <!-- Family Frame -->
            <div class="frame-item">
              <img
                src="../assets/images/intro/FrameFamily.png"
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

<style lang='scss'>
@include font("BlackLagoon", "@/assets/fonts/blackLagoon/BlackLagoon");
h1 {
  font-family: "BlackLagoon";
  color: $primary-font;
}
/* Scene Wrapper */
section {
  height: 100vh;
  width: 100vw;
  background-image: url("../assets/images/bkg/bricks.png");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
/* Frame */
.frame {
  position: relative;
  top: 0%;
  width: 100%;
  height: 100vh;
  &-item {
    position: absolute;
    width: 275px;
    height: auto;
    img {
      display: block;
      width: 100%;
      height: auto;
    }
    &:nth-child(1) {
      left: 2%;
      top: 2%;
    }
    &:nth-child(2) {
      bottom: 2%;
      left: 5%;
    }
    &:nth-child(3) {
      top: 40%;
      left: 50%;
    }
  }
}
</style>
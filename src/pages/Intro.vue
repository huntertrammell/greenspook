<template>
  <section
    class="section-intro"
    role="contentinfo"
    aria-label="Poem introduction"
  >
    <div class="container-fluid p-0">
      <!-- Row -->
      <div class="mobile-stack row">
        <!-- column -->
        <div
          class="mobile-stack_item mobile-stack_item--top col-md-12 col-lg-6"
        >
          <!-- INTRO TEXT -->
          <div class="intro-menu">
            <div class="p-1 text-center title">
              <transition-group
                tag="h1"
                appear
                @before-enter="beforeEnter"
                @enter="enter"
              >
                <span
                  v-for="(icon, index) in icons"
                  :key="icon.text"
                  :data-index="index"
                >
                  {{ icon.text }}
                </span>
              </transition-group>
              <!-- <h1>ColD<br />WinteR<br />NighT</h1> -->
            </div>
          </div>
        </div>
        <!-- column -->
        <div class="mobile-stack_item col-md-12 col-lg-6">
          <!-- Position Relative -->
          <div class="frame">
            <!-- Couple Frame Position Absolute-->
            <FrameItem gsapSelector="couple">
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
                class="gs-lighting_person"
                src="/assets/images/intro/couple/Women_COUPLE_Only.png"
                alt="Women in couple picture"
                width="460"
                height="669"
              />
              <div
                class="frame-item_clip-path frame-item_clip-path--couple"
              ></div>
              <!-- Couple Frame -->
              <img
                src="/assets/images/intro/couple/FRAME_For_COUPLE.png"
                alt="Frame for couple picture"
                width="460"
                height="669"
              />
            </FrameItem>

            <!-- Fisherman Frame -->
            <FrameItem gsapSelector="fisher">
              <img
                src="/assets/images/intro/Fisher_man/BG_Fishing.png"
                alt="picture BG"
                width="622"
                height="536"
              />

              <img
                src="/assets/images/intro/Fisher_man/Tree_Fishing.png"
                alt="couple in picture"
                width="622"
                height="536"
              />
              <img
                src="/assets/images/intro/Fisher_man/Water_Fishing.png"
                alt="couple in picture"
                width="622"
                height="536"
              />
              <img
                class="gs-lighting_person"
                src="/assets/images/intro/Fisher_man/Fishing_Man.png"
                alt="couple in picture"
                width="622"
                height="536"
              />
              <div
                class="frame-item_clip-path frame-item_clip-path--fisher"
              ></div>
              <img
                src="/assets/images/intro/Fisher_man/Frame_Fishing.png"
                alt="couple in picture"
                width="622"
                height="536"
              />
            </FrameItem>
            <!-- Family Frame -->
            <FrameItem gsapSelector="family">
              <img
                src="/assets/images/intro/Family/BG_Family.png"
                alt="couple in picture"
                width="679"
                height="592"
              />
              <img
                class="gs-lighting_person"
                src="/assets/images/intro/Family/Man_Family.png"
                alt="couple in picture"
                width="679"
                height="592"
              />
              <img
                src="/assets/images/intro/Family/Women_Kid_Family.png"
                alt="couple in picture"
                width="679"
                height="592"
              />
              <img
                src="/assets/images/intro/Family/Woman_Hand_Family.png"
                alt="couple in picture"
                width="679"
                height="592"
              />
              <img
                class="gs-lighting_person"
                src="/assets/images/intro/Family/Man_Hand_Family.png"
                alt="couple in picture"
                width="679"
                height="592"
              />
              <div
                class="frame-item_clip-path frame-item_clip-path--family"
              ></div>

              <img
                src="/assets/images/intro/Family/Frame_Family.png"
                alt="couple in picture"
                width="679"
                height="592"
              />
            </FrameItem>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@include font("BlackLagoon", "@/assets/fonts/blackLagoon/BlackLagoon");
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
    font-family: "BlackLagoon";
    color: $primary-font;
    font-size: 8rem;
    line-height: 0.76;
    letter-spacing: 0.2rem;
    display: flex;
    flex-direction: column;
    text-align: center;
    align-items: center;
    justify-content: center;
    padding: 0;
    margin: 0;
    span {
      color: $primary-font;
      font-weight: 600;
      @media (max-width: $md) {
        font-size: 6rem;
      }
    }
  }
}

/* Scene Wrapper */
section {
  background-image: url("../assets/images/bkg/bricks.png");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
</style>

<script>
import { ref } from "vue";
import gsap from "gsap";
import FrameItem from "../components/frame.vue";
export default {
  setup() {
    const icons = ref([
      {
        text: "ColD",
      },
      {
        text: "WinteR",
      },
      {
        text: "NighT",
      },
    ]);
    const beforeEnter = (el) => {
      console.log("before enter");
      el.style.opacity = 0;
      el.style.transform = "translateY(100px)";
    };
    const enter = (el, done) => {
      console.log("Starting to enter -,make transition");
      gsap.to(el, {
        opacity: 1,
        y: 0,
        duration: 0.8,
        onComplete: done,
        delay: el.dataset.index * 0.2,
      });
    };
    return { icons, beforeEnter, enter };
  },
  components: {
    FrameItem,
  },
};
</script>
<template>
  <div class="home scroller">
    <header>
      <p class="header-icon">
        <span class="material-symbols-outlined">grade</span>
      </p>
    </header>

    <section class="section-title">
      <p class="p-section-title"></p>
    </section>

    <section class="section">
      <div class="card-section">
        <img src="@/assets/images/planet.jpg" alt="" />
        <p class="p-section right p-section-color-1">
          Des planètes à perte de vue.
        </p>
      </div>
    </section>

    <section class="section-reverse">
      <div class="card-section-reverse">
        <img src="@/assets/images/moon.jpg" alt="" />
        <p class="p-section left p-section-color-1">
          Comme vous ne les avez jamais vu.
        </p>
      </div>
    </section>

    <section class="section">
      <div class="card-section">
        <img src="@/assets/images/planet.jpg" alt="" />
        <p class="p-section right p-section-color-1">
          Des planètes à perte de vue.
        </p>
      </div>
    </section>
  </div>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { TextPlugin } from "gsap/TextPlugin";
import { ScrollToPlugin } from "gsap/ScrollToPlugin";
gsap.registerPlugin(ScrollTrigger, TextPlugin, ScrollToPlugin);
import Scrollbar from "smooth-scrollbar";

export default {
  data() {
    return {};
  },
  methods: {
    animTitle() {
      const tl = gsap.timeline();

      tl.to(".p-section-title", {
        opacity: 1,
        text: {
          value: "Entrez dans l'espace.",
          speed: 0.6,
        },
        delay: 1,
      });

      tl.to(".p-section-title", {
        className: "p-section-title pulse",
        delay: 0.9,
      });

      tl.play();
    },
    animScrollRight() {
      gsap.utils.toArray(".right").forEach((el) => {
        ScrollTrigger.create({
          trigger: el,
          start: "bottom bottom",
          end: "top top",
          onEnter: function () {
            console.log("ok");
            el.style.transform = "translateX(100px)";
            el.style.transition = "transform 0.5s ease-in-out";
          },
          onLeave: function () {
            console.log("ko");
          },
          onLeaveBack: function () {
            console.log("leaveback");
            el.style.transform = "translateX(0)";
          },
          onEnterBack: function () {
            console.log("enterback");
            el.style.transform = "translateX(0px)";
          },
        });
      });
    },
    animScrollLeft() {
      gsap.utils.toArray(".left").forEach((el) => {
        ScrollTrigger.create({
          trigger: el,
          start: "bottom bottom",
          end: "top top",
          onEnter: function () {
            console.log("ok");
            el.style.transform = "translateX(-100px)";
            el.style.transition = "transform 0.5s ease-in-out";
          },
          onLeave: function () {
            console.log("ko");
          },
          onLeaveBack: function () {
            console.log("leaveback");
            el.style.transform = "translateX(0)";
          },
          onEnterBack: function () {
            console.log("enterback");
            el.style.transform = "translateX(0px)";
            el.style.transition = "transform 0.5s ease-in-out";
          },
        });
      });
    },
    scroll() {
      // Setup
      const scroller = document.querySelector(".scroller");

      const bodyScrollBar = Scrollbar.init(scroller, {
        damping: 0.005,
        delegateTo: document,
        alwaysShowTracks: true,
        renderByPixels: true,
      });

      ScrollTrigger.scrollerProxy(".scroller", {
        scrollTop(value) {
          if (arguments.length) {
            bodyScrollBar.scrollTop = value;
          }
          return bodyScrollBar.scrollTop;
        },
      });

      bodyScrollBar.addListener(ScrollTrigger.update);

      ScrollTrigger.defaults({ scroller: scroller });

      this.animScrollRight();
      this.animScrollLeft();
    },
  },
  mounted() {
    this.animTitle();
    this.scroll();
  },
};
</script>

<style lang="scss">
:root {
  --gradient-1: linear-gradient(-45deg, crimson, rgb(66, 47, 112));
  --gradient-2: linear-gradient(4deg, crimson, orange);

  --font-section: "Poppins", sans-serif;
}
.scroller {
  height: 100vh;
}
.home {
  display: flex;
  flex-direction: column;
  & header {
    display: flex;
    justify-content: flex-end;
    & .material-symbols-outlined {
      font-size: clamp(18px, 2vw, 40px);
    }
    & .header-icon {
      padding: 1%;
      background: var(--gradient-1);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      font-size: clamp(12px, 1vw, 90px);
    }
  }
  & .section-title {
    height: 45vh;
    margin-top: 5%;
    & .p-section-title {
      width: 60vw;
      margin: auto;
      background: var(--gradient-2);
      background-clip: text;
      -webkit-background-clip: text;
      font-family: var(--font-section);
      font-size: clamp(30px, 9vw, 90px);
      color: transparent;
      word-spacing: 100vw;
      opacity: 0;
    }
    & .pulse {
      animation: pulse 1s ease-in-out;
    }
  }
  & .section,
  .section-reverse {
    margin: 5% 0;
    & .card-section {
      display: flex;
      width: 70vw;
      margin: auto;
    }
    & .card-section-reverse {
      display: flex;
      flex-direction: row-reverse;
      width: 70vw;
      margin: auto;
    }
    & img {
      width: 40%;
      height: auto;
      border-radius: 5px;
    }
    & .p-section-color-1 {
      background: var(--gradient-1);
    }
    & .p-section {
      width: 30%;
      margin: auto;
      font-family: var(--font-section);
      font-size: clamp(15px, 4vw, 90px);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
    }
  }
}

// KEYFRAMES //
@keyframes pulse {
  0% {
    filter: blur(0px);
  }
  50% {
    filter: blur(2px);
  }
  100% {
    filter: blur(0px);
  }
}
</style>

<template>
  <div class="home scroller">
    <svg class="svg" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320">
      <defs>
        <linearGradient id="MyGradient">
          <stop offset="25%" stop-color="rgb(20, 14, 34)" id="stop" />
          <stop offset="80%" stop-color="rgb(20, 0, 7)" id="stop2" />
        </linearGradient>
      </defs>
      <path
        fill="url(#MyGradient)"
        fill-opacity="1"
        d="M0,288L60,256C120,224,240,160,360,117.3C480,75,600,53,720,53.3C840,53,960,75,1080,85.3C1200,96,1320,96,1380,96L1440,96L1440,0L1380,0C1320,0,1200,0,1080,0C960,0,840,0,720,0C600,0,480,0,360,0C240,0,120,0,60,0L0,0Z"
      >
        <p class="header-icon">
          <span class="material-symbols-outlined">grade</span>
        </p>
      </path>
    </svg>

    <section class="section-title">
      <p class="p-section-title"></p>
    </section>

    <section class="section">
      <div class="card-section">
        <div class="container-img">
          <img src="@/assets/images/planet.jpg" alt="" />
        </div>
        <p class="p-section right p-section-color-1">
          Des planètes à perte de vue.
        </p>
      </div>
    </section>

    <section class="section-reverse">
      <div class="card-section-reverse">
        <div class="container-img">
          <img src="@/assets/images/moon.jpg" alt="" />
        </div>
        <p class="p-section left p-section-color-1">
          Comme vous ne les avez jamais vu.
        </p>
      </div>
    </section>

    <section class="section">
      <div class="card-section">
        <div class="container-img">
          <img src="@/assets/images/planet.jpg" alt="" />
        </div>
        <p class="p-section right p-section-color-1">
          Des planètes à perte de vue.
        </p>
      </div>
    </section>
    <footer>
      <div>
        <a href="mailto:byfabe@gmail.com">
          <i class="fa-solid fa-envelope mail-icon"></i>
        </a>
        <a
          href="https://www.rivetportfolio.ovh/"
          target="_blank"
          rel="noopener noreferrer"
        >
          <span>PORTFOLIO</span></a
        >
      </div>
    </footer>
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
    animTextRight() {
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
    animTextLeft() {
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
    animImage() {
      gsap.utils.toArray("img").forEach((el) => {
        ScrollTrigger.create({
          trigger: el,
          start: "top center",
          end: "bottom bottom",
          onEnter: function () {
            el.style.transform = "scale(2)";
            el.style.transition = "transform 1.5s ease-in-out";
          },
          onLeave: function () {},
          onLeaveBack: function () {},
          onEnterBack: function () {
            el.style.transform = "scale(1)";
            el.style.transition = "transform 1.5s ease-in-out";
          },
        });
      });
    },
    animBG() {
      gsap.to(".home", {
        backgroundImage:
          "linear-gradient(-45deg, rgb(46, 1, 16) 0%, rgb(32, 22, 54))",
        duration: 6,
        ease: "none",
        scrollTrigger: {
          trigger: ".scroll-content",
          start: "top top",
          end: "bottom bottom",
          scrub: 1,
        },
      });

      // gsap.utils.toArray("img").forEach((el) => {
      //   ScrollTrigger.create({
      //     trigger: el,
      //     markers: true,
      //     start: "top center",
      //     end: "bottom bottom",
      //     onEnter: () => {
      //       gsap.to(".home", {
      //         duration: 3.0,
      //         background:
      //           "linear-gradient(-45deg, rgb(20, 0, 7), rgb(20, 14, 34))",
      //       });
      //     },
      //     onEnterBack: () => {
      //       gsap.to(".home", {
      //         duration: 3.0,
      //         background:
      //           "linear-gradient(45deg, rgb(20, 0, 7), rgb(20, 14, 34))",
      //       });
      //     },
      //   });
      // });
    },
    animSVG() {
      gsap.to("#stop", {
        stopColor: "rgb(85, 9, 24)",
        ease: "none",
        duration: 20,
        repeat: -1,
        yoyo: true,
      });
      gsap.to("#stop2", {
        stopColor: "rgb(220, 20, 60)",
        ease: "none",
        duration: 20,
        repeat: -1,
        yoyo: true,
      });
    },
    scroll() {
      // Setup
      const scroller = document.querySelector(".scroller");

      const bodyScrollBar = Scrollbar.init(scroller, {
        damping: 0.01,
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

      this.animTextRight();
      this.animTextLeft();
      this.animImage();
    },
  },
  mounted() {
    this.animTitle();
    this.scroll();
    this.animBG();
    this.animSVG();
  },
};
</script>

<style lang="scss">
:root {
  --gradient-1: linear-gradient(-45deg, rgb(220, 20, 60), rgb(66, 47, 112));
  --gradient-2: linear-gradient(4deg, crimson, rgb(139, 102, 33));

  --font-section: "Poppins", sans-serif;
}
.scroller {
  height: 100vh;
}
.home {
  display: flex;
  flex-direction: column;
  & .svg {
    position: absolute;
    z-index: -1;
  }
  & .header-icon {
    position: absolute;
    right: 0;
    top: .5%;
    display: flex;
    align-items: center;
    padding: 1%;
    background: var(--gradient-2);
    background-clip: text;
    -webkit-background-clip: text;
    color: transparent;
    font-size: clamp(12px, 1vw, 90px);
    & .material-symbols-outlined {
      font-size: clamp(18px, 2vw, 40px);
    }
  }
  // & header {
  //   display: flex;
  //   justify-content: flex-end;
  //   align-items: center;
  //   height: 6vh;
  //   background: linear-gradient(-45deg, rgb(20, 0, 7), #140e22);
  //   box-shadow: rgba(0, 0, 0, 0.15) 0px 3px 3px 0px;
  // }
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
    & .container-img {
      width: 40%;
      overflow: hidden;
      border-radius: 10px;
      & img {
        width: 100%;
        height: auto;
      }
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
  & footer {
    & div {
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: var(--font-section);
      margin: 0.5%;
      & a {
        text-decoration: none;
        color: #862358;
      }
      & a:nth-child(1) {
        margin-right: 1%;
      }
      & i,
      span {
        cursor: pointer;
      }
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



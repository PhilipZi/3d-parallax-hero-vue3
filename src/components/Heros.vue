<template>
  <main class="layout" :style="{ 'max-height': screenWidth }">
    <div class="vignette"></div>
    <img
      src="../assets/img/background.png"
      data-speedx="0.3"
      data-speedy="0.38"
      data-speedz="0"
      data-rotation="0"
      data-distance="-200"
      class="parallax bg-img"
    />
    <img
      src="../assets/img/fog_7.png"
      data-speedx="0.27"
      data-speedy="0.32"
      data-speedz="0"
      data-rotation="0"
      data-distance="850"
      class="parallax fog-7"
    />
    <img
      src="../assets/img/mountain_10.png"
      data-speedx="0.195"
      data-speedy="0.305"
      data-speedz="0"
      data-rotation="0"
      data-distance="1100"
      class="parallax mountain-10"
    />
    <img
      src="../assets/img/fog_6.png"
      data-speedx="0.25"
      data-speedy="0.28"
      data-speedz="0"
      data-rotation="0"
      data-distance="1400"
      class="parallax fog-6"
    />
    <img
      src="../assets/img/mountain_9.png"
      data-speedx="0.125"
      data-speedy="0.155"
      data-speedz="0.15"
      data-rotation="0.02"
      data-distance="1700"
      class="parallax mountain-9"
    />
    <img
      src="../assets/img/mountain_8.png"
      data-speedx="0.1"
      data-speedy="0.11"
      data-speedz="0"
      data-rotation="0.02"
      data-distance="1800"
      class="parallax mountain-8"
    />
    <img
      src="../assets/img/fog_5.png"
      data-speedx="0.16"
      data-speedy="0.105"
      data-speedz="0"
      data-rotation="0"
      data-distance="1900"
      class="parallax fog-5"
    />
    <img
      src="../assets/img/mountain_7.png"
      data-speedx="0.1"
      data-speedy="0.1"
      data-speedz="0"
      data-rotation="0.09"
      data-distance="2000"
      class="parallax mountain-7"
    />
    <div
      class="text parallax"
      data-speedx="0.07"
      data-speedy="0.07"
      data-speedz="0"
      data-rotation="0.11"
      data-distance="0"
    >
      <h2>This is</h2>
      <h1>Homepage</h1>
    </div>
    <img
      src="../assets/img/mountain_6.png"
      data-speedx="0.065"
      data-speedy="0.05"
      data-speedz="0.05"
      data-rotation="0.1"
      data-distance="2300"
      class="parallax mountain-6"
    />
    <img
      src="../assets/img/fog_4.png"
      data-speedx="0.135"
      data-speedy="0.035"
      data-speedz="0"
      data-rotation="0.11"
      data-distance="2400"
      class="parallax fog-4"
    />
    <img
      src="../assets/img/mountain_5.png"
      data-speedx="0.08"
      data-speedy="0.05"
      data-speedz="0.15"
      data-rotation="0.17"
      data-distance="2550"
      class="parallax mountain-5"
    />
    <img
      src="../assets/img/fog_3.png"
      data-speedx="0.11"
      data-speedy="0.018"
      data-speedz="0.15"
      data-rotation="0"
      data-distance="2800"
      class="parallax fog-3"
    />
    <img
      src="../assets/img/mountain_4.png"
      data-speedx="0.059"
      data-speedy="0.024"
      data-speedz="0"
      data-rotation="0.18"
      data-distance="3200"
      class="parallax mountain-4"
    />
    <img
      src="../assets/img/mountain_3.png"
      data-speedx="0.04"
      data-speedy="0.018"
      data-speedz="0.32"
      data-rotation="0.2"
      data-distance="3400"
      class="parallax mountain-3"
    />
    <img
      src="../assets/img/fog_2.png"
      data-speedx="0.15"
      data-speedy="0.0115"
      data-speedz="0"
      data-rotation="0.22"
      data-distance="3600"
      class="parallax fog-2"
    />
    <img
      src="../assets/img/mountain_2.png"
      data-speedx="0.0235"
      data-speedy="0.013"
      data-speedz="0"
      data-rotation="0.27"
      data-distance="3800"
      class="parallax mountain-2"
    />
    <img
      src="../assets/img/mountain_1.png"
      data-speedx="0.027"
      data-speedy="0.018"
      data-speedz="0.53"
      data-rotation="0.3"
      data-distance="4000"
      class="parallax mountain-1"
    />
    <img src="../assets/img/sun_rays.png" class="sun-rays" />
    <img src="../assets/img/black_shadow.png" class="black-shadow" />
    <img
      src="../assets/img/fog_1.png"
      data-speedx="0.12"
      data-speedy="0.01"
      data-speedz="0"
      data-rotation="0"
      data-distance="4200"
      class="parallax fog-1"
    />
  </main>
</template>

<script setup>
import { ref, onMounted, onBeforeMount, onUpdated } from "vue";
import { gsap } from "gsap";

const parallax_el = ref([]);
let screenWidth = ref();
let timeline = gsap.timeline();

let xValue = 0,
  yValue = 0;

let rotateDegree = 0;

const update = (cursorPosition) => {
  parallax_el.value.forEach((el) => {
    let speedx = el.dataset.speedx;
    let speedy = el.dataset.speedy;
    let speedz = el.dataset.speedz;
    let rotateSpeed = el.dataset.rotation;

    let isInLeft =
      parseFloat(getComputedStyle(el).left) < window.innerWidth / 2 ? 1 : -1;

    let zValue =
      (cursorPosition - parseFloat(getComputedStyle(el).left)) * isInLeft * 0.1;

    el.style.transform = `translateX(calc(-50% + ${
      -xValue * speedx
    }px)) translateY(calc(-50% + ${yValue * speedy}px)) rotateY(${
      rotateDegree * rotateSpeed
    }deg)  perspective(2300px) translateZ(${zValue * speedz}px)`;
  });
};

// checks if the screen has to be resized
onBeforeMount(() => {
  if (window.innerWidth >= 725) {
    screenWidth = `${window.innerWidth * 0.6}px`;
  } else {
    screenWidth = `${window.innerWidth * 1.6}px`;
  }
});

onMounted(() => {
  parallax_el.value = Array.from(document.querySelectorAll(".parallax"));

  parallax_el.value
    .filter((el) => !el.classList.contains("text"))
    .forEach((el) => {
      timeline.from(
        el,
        {
          top: `${el.offsetHeight / 2 + +el.dataset.distance}px`,
          duration: 3.5,
          ease: "power3.out",
        },
        "1"
      );
    });

  timeline
    .from(
      ".text h1",
      {
        y:
          window.innerHeight -
          document.querySelector(".text h1").getBoundingClientRect().top,
        duration: 2,
      },
      "2.5"
    )
    .from(
      ".text h2",
      {
        y: -150,
        opacity: 0,
        duration: 1.5,
      },
      "3"
    )
    .from(
      ".hide",
      {
        opacity: 0,
        duration: 1.5,
      },
      "3"
    );

  update(0);
  setTimeout(() => {
    window.addEventListener("mousemove", onMouseMove);
  }, 5000);
});

const onMouseMove = (e) => {
  xValue = e.clientX - window.innerWidth / 2;
  yValue = e.clientY - window.innerHeight / 2;

  rotateDegree = (xValue / (window.innerWidth / 2)) * 20;

  update(e.clientX);
};
</script>

<style scoped>
main {
  position: relative;
  height: 100vh;
  width: 100vw;
  overflow: hidden;
}

.parallax {
  pointer-events: none;
  transition: none;
}

.bg-img {
  position: absolute;
  width: 194.44%;
  top: 1.86%;
  left: 50.69%;
  z-index: 1;
}

.fog-7 {
  position: absolute;
  z-index: 2;
  width: 132%;
  top: 37.7%;
  left: 52.08%;
}

.fog-1 {
  position: absolute;
  width: 111.8%;
  top: 59.26%;
  left: 50.69%;
  z-index: 21;
}
.mountain-10 {
  position: absolute;
  z-index: 3;
  top: 58.51%;
  width: 60.41%;
  left: 65.97%;
}
.fog-2 {
  position: absolute;
  z-index: 4;
  top: 61.17%;
  left: 50.48%;
  width: 127.29%;
}

.mountain-9 {
  position: absolute;
  z-index: 5;
  top: 64.69%;
  width: 32.15%;
  left: 18.27%;
}

.mountain-8 {
  position: absolute;
  z-index: 6;
  top: 61.85%;
  width: 54.58%;
  left: 35.98%;
}

.fog-3 {
  position: absolute;
  z-index: 7;
  top: 71.11%;
  left: 52.01%;
  width: 31.18%;
}
.mountain-7 {
  position: absolute;
  z-index: 8;
  width: 35.76%;
  top: 66.54%;
  left: 71.18%;
}

.mountain-6 {
  position: absolute;
  z-index: 10;
  top: 60.67%;
  width: 26.63%;
  left: 90.97%;
}

.fog-4 {
  position: absolute;
  z-index: 11;
  top: 79.87%;
  left: 45.56%;
  width: 37.7%;
}

.mountain-5 {
  position: absolute;
  z-index: 12;
  top: 83.2%;
  width: 40.48%;
  left: 59.02%;
}

.fog-5 {
  position: absolute;
  z-index: 13;
  top: 68.39%;
  left: 48.06%;
  width: 99.65%;
}

.mountain-4 {
  position: absolute;

  z-index: 14;
  top: 77.28%;
  width: 49.79%;
  left: 23.51%;
}

.mountain-3 {
  position: absolute;

  z-index: 15;
  top: 66.41%;
  left: 101.11%;
  width: 29.09%;
}
.fog-6 {
  position: absolute;

  z-index: 10;
  top: 71.85%;
  left: 47.92%;
  width: 98.47%;
}
.mountain-2 {
  position: absolute;

  z-index: 17;
  top: 73.2%;
  left: 78.61%;
  width: 43.4%;
}
.mountain-1 {
  position: absolute;
  z-index: 18;
  top: 60%;
  left: 8.27%;
  width: 31.25%;
}

.text {
  position: absolute;
  z-index: 9;
  top: calc(50% - 130px);
  left: 50%;

  text-align: center;
  text-transform: uppercase;
  color: #fff;
  pointer-events: auto;
}

.text h2 {
  font-weight: 100;
  font-size: 6.5rem;
  line-height: 0.88;
  pointer-events: auto;
}

.text h1 {
  font-weight: 800;
  font-size: 8rem;
  line-height: 0.88;
  pointer-events: auto;
}

.sun-rays {
  position: absolute;
  z-index: 19;
  top: 0;
  right: 0;
  width: 595px;
  pointer-events: none;
}

.black-shadow {
  position: absolute;
  z-index: 20;
  bottom: 0;
  right: 0;
  width: 100%;
  pointer-events: none;
}

.vignette {
  position: absolute;
  z-index: 100;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background: radial-gradient(
    ellipse at center,
    rgba(0, 0, 0, 0) 65%,
    rgba(0, 0, 0, 0.7)
  );
  pointer-events: none;
}

@media (max-width: 1100px) {
  .text h1 {
    font-size: 5.8rem;
  }

  .text h2 {
    font-size: 4.7rem;
  }
}
@media (max-width: 725px) {
  .text {
    top: 25%;
  }

  .text h1 {
    font-size: 5rem;
    line-height: 1.1;
  }

  .text h2 {
    font-size: 4.1rem;
    line-height: 1.1;
  }

  header nav {
    padding: 0 1rem;
  }

  .logo {
    width: 75px;
  }

  header ul a {
    font-size: 0.73rem;
    padding: 0 0.9rem;
  }

  .search a {
    font-size: 0.85rem;
    padding: 0 1.8rem;
  }

  .hamburger {
    padding-left: 0.9rem;
  }

  .hamburger a {
    width: 30px;
    height: 30px;
  }

  .bg-img {
    width: initial;
    height: 311.104%;
  }
  .fog-7 {
    width: initial;
    height: 211.2%;
  }
  .fog-1 {
    width: initial;
    height: 178.88%;
  }
  .mountain-10 {
    width: initial;
    height: 96.656%;
  }
  .fog-2 {
    width: initial;
    height: 203.664%;
  }
  .mountain-9 {
    width: initial;
    height: 51.44%;
  }
  .mountain-8 {
    width: initial;
    height: 87.328%;
  }
  .fog-3 {
    width: initial;
    height: 49.888%;
  }
  .mountain-7 {
    width: initial;
    height: 57.216%;
  }
  .mountain-6 {
    width: initial;
    height: 102.216%;
  }
  .fog-4 {
    width: initial;
    height: 60.32%;
  }
  .mountain-5 {
    width: initial;
    height: 64.768%;
  }
  .fog-5 {
    width: initial;
    height: 159.44%;
  }
  .mountain-4 {
    width: initial;
    height: 79.664%;
  }
  .mountain-3 {
    width: initial;
    height: 67.88%;
  }
  .fog-6 {
    width: initial;
    height: 157.552%;
  }
  .mountain-2 {
    width: initial;
    height: 69.44%;
  }
  .mountain-1 {
    width: initial;
    height: 87%;
  }
}

@media (max-width: 520px) {
  .text h1 {
    font-size: 3.3rem;
  }

  .text h2 {
    font-size: 2.6rem;
  }
}
</style>

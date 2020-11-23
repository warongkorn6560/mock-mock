<template>
  <div class="h-full">
    <!-- header -->
    <div class="top-header grid grid-cols-12 grid-flow-col items-center">
      <div
        class="col-start-12 h-full w-full header-hover cursor-pointer"
        @click="saveAs()"
      >
        <img :src="downloadIcon" class="mx-auto h-full py-3" />
      </div>
    </div>
    <!-- fabric -->
    <div class="z-0"><Fabric /></div>
    <!-- swiper -->
    <div class="w-full items-center bot-header">
      <ContentSwiper
        id="frame"
        hasPagination
        hasNavigation
        :swiperOption="{
          slidesPerView: 1,
          breakpoints: {
            768: {
              slidesPerView: 5,
            },
          },
        }"
      >
        <div
          v-for="(item, i) in imgSlide"
          :key="`item-${i}`"
          class="block preload swiper-slide"
        >
          <div
            class="shadow-lg m-4 p-8 rounded-lg cursor-pointer frame-card transform hover:scale-125 hover:-translate-y-4 hover:scale-x-150 hover:z-10 flex justify-center items-center"
          >
            <div
              :style="{ backgroundImage: `url(${item})` }"
              class="w-full slide-img p-4"
            ></div>
            <div class="hide-card text-bold">model:xxxxx</div>
          </div>
        </div>
      </ContentSwiper>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    selectedFrame: null,
    imgSlide: [
      "ipad-pro-landscape.webp",
      "ipad-pro.webp",
      "iphone-x-2-scr.webp",
      "iphone-x-2.webp",
      "iphone-x-front.webp",
      "iphone-x.webp",
      "iphone-xr-right.webp",
      "pixel-duo.webp",
    ],
    downloadIcon: "download.svg",
  }),
  methods: {
    selectFrame(i) {
      this.selectedFrame = +i;
      console.log(this.selectedFrame);
    },
    saveAs() {
      const canvas = document.getElementById("canvas");
      canvas.toBlob(function (blob) {
        saveAs(blob, "mock-mock.png");
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.slide-img {
  position: relative;
  padding-bottom: 100%;
  @apply bg-contain bg-no-repeat bg-center w-full;
  @screen md {
    padding-bottom: 40%;
  }
}
.top-header {
  width: 100%;
  height: 4rem;
  box-shadow: 2px 5px 50px rgba(rgb(116, 109, 109), 0.2);
  z-index: 10;
  background-color: #ffffff;
}

.bot-header {
  box-shadow: 2px 5px 50px rgba(rgb(116, 109, 109), 0.2);
  background-color: #ffffff;
  z-index: 10;
}

.turn-red {
  &:hover {
    filter: invert(48%) sepia(53%) saturate(7143%) hue-rotate(328deg)
      brightness(99%) contrast(88%);
  }
}
.header-hover {
  &:hover {
    transition: 0.4s;
    background-color: #ed3f64;
    img {
      transition: 0.4s;
      filter: brightness(0) invert(1);
    }
  }
}

.frame-card {
  &:hover {
    transition: 0.4s;
    background-color: #ed3f64;
    .slide-img {
      transform: translateX(-24px);
      transition: 0.7s;
    }
    .hide-card {
      transform: translateX(10px);
      font-family: "Lato", sans-serif;
      transition: 0.7s;
      display: block;
      color: white;
    }
  }
}

.hide-card {
  display: none;
}
</style>
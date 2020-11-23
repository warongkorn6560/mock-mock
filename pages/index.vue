<template>
  <div class="h-full">
    <div class="top-header grid grid-cols-12 grid-flow-col items-center">
      <div class="col-start-12 h-full w-full turn-red">
        <img
          :src="downloadIcon"
          @click="saveAs()"
          class="cursor-pointer mx-auto h-full py-3 turn-red"
        />
      </div>
    </div>
    <div><Fabric /></div>
    <div class="w-full bg-gray-400 h-full">
      <ContentSwiper
        id="frame"
        hasPagination
        hasNavigation
        :swiperOption="{
          slidesPerView: 1,
          breakpoints: {
            768: {
              slidesPerView: 4,
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
            :style="{ backgroundImage: `url(${item})` }"
            class="slide-img banner-img"
          ></div>
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
.banner-img {
  position: relative;
  padding-bottom: 100%;
  @apply bg-contain bg-no-repeat bg-center w-full;
  @screen md {
    padding-bottom: 34.84%;
  }
}
.top-header {
  width: 100%;
  height: 4rem;
  background: #f5f5f5;
  box-shadow: 2px 5px 50px rgba(grey, 0.2);
  z-index: 10;
}

.turn-red {
  &:hover {
    filter: invert(48%) sepia(53%) saturate(7143%) hue-rotate(328deg)
      brightness(99%) contrast(88%);
  }
}
</style>
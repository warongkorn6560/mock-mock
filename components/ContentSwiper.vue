<template>
  <client-only>
    <div v-swiper:mySwiper="_swiperOption">
      <div class="swiper-wrapper">
        <slot></slot>
      </div>
      <div
        v-if="hasPagination"
        slot="pagination"
        class="swiper-pagination"
      ></div>
      <img
        v-if="hasNavigation"
        class="swiper-button-prev transform -rotate-90 arrowHover"
        :class="`prev-${this.id}`"
        :src="arrow"
      />
      <img
        v-if="hasNavigation"
        class="swiper-button-next transform rotate-90 arrowHover"
        :class="`next-${this.id}`"
        :src="arrow"
      />
    </div>
  </client-only>
</template>

<script>
import { directive } from "vue-awesome-swiper";
import "assets/css/_swiper.scss";

export default {
  directives: {
    swiper: directive,
  },
  props: {
    swiperOption: {
      type: Object,
      default: () => {},
    },
    hasPagination: {
      type: Boolean,
      default: false,
    },
    hasNavigation: {
      type: Boolean,
      default: false,
    },
    hasAutoplay: {
      type: Boolean,
      default: false,
    },
  },
  data: () => ({
    arrow: "chevron.svg",
    bulletLength: 0,
    id: null,
    defalutSwiperOption: {
      pagination: {
        el: `.swiper-pagination`,
        clickable: true,
        dynamicBullets: true,
        dynamicMainBullets: 5,
      },
      speed: 600,
      centerInsufficientSlides: true,
      watchOverflow: true,
      freeModeMomentum: true,
      keyboard: {
        enabled: true,
        onlyInViewport: false,
      },
    },
    customSwiperOption: {},
  }),
  computed: {
    _swiper() {
      return this.mySwiper;
    },
    _swiperOption() {
      return {
        ...this.defalutSwiperOption,
        ...this.swiperOption,
        ...this.customSwiperOption,
      };
    },
  },
  created() {
    this.id = `swiper-${~~(Math.random() * 100000)}`;
    if (this.hasNavigation) {
      this.defalutSwiperOption.navigation = {
        nextEl: `.next-${this.id}`,
        prevEl: `.prev-${this.id}`,
      };
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.$emit("instance", this._swiper);
    });

    if (this.hasAutoplay) {
      this.customSwiperOption = {
        speed: 1000,
        loop: false,
        autoplay: {
          delay: 2500,
          disableOnInteraction: false,
        },
      };
    }
  },
};
</script>

<style lang="scss" scoped>
.arrowHover {
  @apply transition duration-500 ease-in-out;
  &:hover {
    @apply scale-110;
  }
}
</style>

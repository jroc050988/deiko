<template>
  <div class="ix__banner">
    <VueSlickCarousel v-bind="settings">
      <div class="item item--1">
        <div class="item__background item__background--1"></div>
        <div class="slogan">
          <p class="title">美味幸福加分</p>
          <p class="subTitle">使用100%純天然食材，絕無添加防腐劑</p>
        </div>
      </div>

      <div class="item item--1">
        <div class="item__background item__background--2"></div>
        <div class="slogan">
          <p class="title">美味幸福加分02</p>
          <p class="subTitle">使用100%純天然食材，絕無添加防腐劑</p>
        </div>
      </div>
    </VueSlickCarousel>
  </div>
</template>
<script>
import VueSlickCarousel from "vue-slick-carousel";
import "vue-slick-carousel/dist/vue-slick-carousel.css";
// optional style for arrows & dots
import "vue-slick-carousel/dist/vue-slick-carousel-theme.css";

export default {
  data() {
    return {
      settings: {
        arrows: true,
        dots: true,
        autoplay: true,
        autoplaySpeed: 8000,
        fade: true,
        speed: 0,
        pauseOnHover: false,
        pauseOnFocus: false,
      },
    };
  },
  name: "ixBannner",
  components: { VueSlickCarousel },
};
</script>

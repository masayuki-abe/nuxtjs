<template>
<section
  v-if="this.$route.name === 'index'"
  id="visual"
  :class=pageName
>
  <client-only>
    <div class="visual-slider">
      <swiper :options="swiperOption">
        <swiper-slide><img src="~/assets/img/index/visual01.jpg" alt="ビジュアル1"></swiper-slide>
        <swiper-slide><img src="~/assets/img/index/visual02.jpg" alt="ビジュアル2"></swiper-slide>
        <swiper-slide><img src="~/assets/img/index/visual03.jpg" alt="ビジュアル3"></swiper-slide>
      </swiper>
    </div>
  </client-only>
  <h2 class="serif">I want to dance again.</h2>
</section>
<section
  v-else
  id="visual"
  class="lower"
  :class=pageName
>
  <h2>{{this.$route.name}}</h2>
</section>
</template>

<script>
export default {
  props: {
  },
  data(){
    return{
      pageName: this.$route.name,
      swiperOption: {
        speed: 3000,
        autoplay: {
          delay: 3000,
          disableOnInteraction: false
        },
        slidePerView: 1,
        loop: true,
        effect: 'fade',
        fadeEffect: {
          crossFade: true
        },
      }
    }
  }
}
</script>

<style lang="scss">
#visual{
  &.index{
    position: relative;
    .swiper-container{
      width: 100%;
      img{
        width: 100%;
        height: auto;
      }
    }
    h2{
      @include dflex(c,c);
      position: absolute;
      left: 0;
      top: 0;
      z-index: 100;
      width: 100%;
      height: 100%;
      color: $milk;
      @include fontSet(42,48,300,$tab);
      font-weight: 400;

    }
  }
}
@include lap(){
}
</style>

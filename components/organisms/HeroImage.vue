<template>
<section
  v-if = "this.$route.name === 'index'"
  id = "visual"
  :class = this.$route.name
  :style = "{top: hHeightPadding}"
>
  <client-only>
    <swiper :options="swiperOption">
      <swiper-slide><img src="~/assets/img/index/visual01.jpg" alt="ビジュアル1"></swiper-slide>
      <swiper-slide><img src="~/assets/img/index/visual02.jpg" alt="ビジュアル2"></swiper-slide>
      <swiper-slide><img src="~/assets/img/index/visual03.jpg" alt="ビジュアル3"></swiper-slide>
    </swiper>
  </client-only>
  <div class="visual-text">
    <h2 id="vt" class="vt2 serif">I want to dance again.</h2>
  </div>
</section>
<section
  v-else
  id="visual"
  class="lower"
  :class = this.$route.name
>
  <h2 class="visual-text serif" style="display:block;">{{this.$route.name}}</h2>
</section>
</template>

<script>
export default {
  props: {
    hHeightPadding: {
      type: String,
    }
  },
  data(){
    return{
      visualPadding: this.hHeightPadding,
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
      },
      visualHeight: 0
    }
  }
}
</script>

<style lang="scss">
#visual{
  position: sticky;
  left: 0;
  top: 0;
  &.index{
    @include dflex(c,c);
    .swiper-container{
      width: 100%;
      height: auto;
      font-size: 0;
      line-height: 0;
      .swiper-wrapper{
        height: auto;
      }
      .swiper-slide{
        overflow: hidden;
        height: auto;
      }
      img{
        width: 100%;
        height: auto;
      }
    }
    .visual-text{
      @include dflex(c,c);
      position: absolute;
      left: 0;
      top: 0;
      z-index: 100;
      width: 100%;
      height: 100%;
      h2{
        @include dflex(c,c);
        color: $milk;
        @include fontSet(42,48,300,$tab);
        font-weight: 400;
      }
    }
  }
  &.blog{
    background: url(~/assets/img/blog/visual.jpg) no-repeat center center; background-size: cover;
    .visual-text{
      padding: 2em 0;
      color: $milk;
      @include fontSet(42,48,400,$tab);
      font-weight: 400;
      @include ta(center);
    }
  }
  &.about{
    background: url(~/assets/img/about/visual.jpg) no-repeat center center; background-size: cover;
    .visual-text{
      padding: 2em 0;
      color: $milk;
      @include fontSet(42,48,400,$tab);
      font-weight: 400;
      @include ta(center);
    }
  }
}
@include lap(){
}
</style>

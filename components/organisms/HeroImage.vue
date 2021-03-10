<template>
<section 
  v-if="this.$route.name === 'index'"
  id="visual"
  class="index"
>
  <swiper :options="swiperOption">
    <swiper-slide>{{this.$route.name}} 1</swiper-slide>
    <swiper-slide>{{this.$route.name}} 2</swiper-slide>
    <swiper-slide>{{this.$route.name}} 3</swiper-slide>
  </swiper>
</section>
<section 
  v-else
  id="visual"
  class="lower"
>
  <h1>{{this.$route.name}}</h1>
</section>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: ''
    }
  },
  data(){
    return{
      swiperOption: {
        speed: 1000,
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
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 200px;
  background-color: #333;
  color: #fff;
  &.lower{
    height: 100px;
    background-color: #ccc;
    color: #333;
  }
  .swiper-container{
    width: 100%;
  }
}
</style>


<template>
<transition name="fadein">
  <aside
    v-show="btnSclTopActive"
    @click="sclTop"
    class="btn-scltop"
  >
    <span></span>
  </aside>
</transition>
</template>

<script>
export default {
  mounted() {
    window.addEventListener('scroll', this.btnFadeIn)
  },
  data() {
    return{
      btnSclTopActive: false,
      scroll: 0
    }
  },
  methods: {
    sclTop() {
      window.scrollTo ({
        top: 0,
        behavior: "smooth"
      })
    },
    btnFadeIn() {
      const top =50
      this.scroll = window.scrollY
      if(top <= this.scroll){
        this.btnSclTopActive = true
      }else{
        this.btnSclTopActive = false
      }
    },
  }
}
</script>

<style lang="scss" scoped>
.btn-scltop{
  position: fixed;
  bottom: 10px;
  right: 10px;
  z-index: 9999;
  &.fadein-enter-active,
  &.fadein-leave-active{
    transition: opacity .4s ease;
  }
  &.fadein-enter,
  &.fadein-leave-to{
    opacity :0;
  }
  span{
    @include dis(inline-block);
    width: 1em;
    height: 1em;
    border-top: 2px $darkBrown solid;
    border-left: 2px $darkBrown solid;
    @include fontSet(32,32,0,$tab);
    transform: rotate(45deg);
  }
}
@include tab() {
.btn-scltop{
  bottom: 20px;
  right: 20px;
}
}
</style>
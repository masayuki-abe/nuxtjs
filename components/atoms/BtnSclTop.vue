<template>
<transition name="fadein">
  <aside
    v-show="btnSclTopActive"
    @click="sclTop"
    class="btn-scltop"
  >
    ページトップへ
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
      const top =100
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
}
</style>
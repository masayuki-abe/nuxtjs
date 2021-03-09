<template>
<header id="header">
  <div class="inner">
    <SiteName htmlTag="h1" />
    <aside
      v-if="isMobile"
      class="btn-menu"
      @click='btnActive = !btnActive'
      :class='{active:btnActive}'
    >
      <span></span>
      <span></span>
      <span></span>
    </aside>
    <transition name="spNavi">
      <NaviBody
        v-if="btnActive || !isMobile"
        role="Gnavi"
        v-on:toHtmlHeader="closeNavi"
      />
    </transition>
  </div>
</header><!--/header-->

</template>

<script>
import SiteName from '@/components/atoms/SiteName.vue';
import NaviBody from '@/components/molecules/NaviBody.vue';

export default {
  components: {
    SiteName,
    NaviBody,
  },
  data(){
    return{
      btnActive: false,
      wWidth: 1025
    }
  },
  mounted(){
    this.wWidth = window.innerWidth
    this.$nextTick(() => {
      window.addEventListener('resize', () => {
        this.wWidth = window.innerWidth
      })
    })
  },
  methods:{
    closeNavi:function () {
      this.btnActive = false
    },
  },
  computed:{
    isMobile(){
      return this.wWidth <= 1024;
    }
  },
}
</script>

<style lang="scss">
#header{
  position: relative;
  padding: 10px 0;
  .inner{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center;
  }
  h1 {
    width: 90%;
    margin: 0;
  }
  .btn-menu {
    position: relative;
    width: 10%;
    span {
      position: absolute;
      left: 0;
      top: 50%;
      display: inline-block;
      width: 100%;
      height: 2px;
      background-color: #333;
      &:nth-child(1){margin-top: -10px;}
      &:nth-child(3){margin-top: 10px;}
    }
  }
  .spNavi-enter-active,
  .spNavi-leave-active {
    opacity: 0;
    transition: opacity .4s ease;
  }
  .spNavi-enter-from,
  .spNavi-leave-to {
    opacity: 0;
  }
  .spNavi-enter-to,
  .spNavi-leave-from {
    opacity: 1;
  }
}
</style>
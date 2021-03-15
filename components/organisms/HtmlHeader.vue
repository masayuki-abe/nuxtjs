<template>
<header
  id="header"
  :class="{opacity : headerBg}"
>
  <div class="inner">
    <SiteName htmlTag="hlogo" />
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
      wWidth: 1025,
      headerHeight: 0,
      headerBg: false,
      scroll: 0
    }
  },
  mounted(){
    //リサイズしたとき含めてヘッダの高さを取得
    let htmlHeader = document.getElementById('header');
    let hHeight = htmlHeader.clientHeight;
    this.headerHeight = hHeight
    //リサイズしたとき含めてウィンドウの横幅を取得
    this.wWidth = window.innerWidth
    this.$nextTick(() => {
      window.addEventListener('resize', () => {
        this.wWidth = window.innerWidth
        this.headerHeight = hHeight
      })
    })
    window.addEventListener('scroll', this.headerBgColor)
    console.log(this.headerHeight + 'px')
    this.$emit('getHeaderHeight',this.headerHeight)
  },
  methods:{
    //ハンバーガーメニューの処理
    closeNavi:function () {
      this.btnActive = false
    },
    headerBgColor() {
      const top =50
      this.scroll = window.scrollY
      if(top <= this.scroll){
        this.headerBg = true
      }else{
        this.headerBg = false
      }
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
  position: sticky;
  left: 0;
  top: 0;
  z-index: 10000;
  width: 100%;
  background-color: $darkBrown;
  padding: 10px 0;
  transition: background .6s ease;
  &.opacity{
    background-color: rgba($darkBrown,.9);
  }
  .inner{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center;
    padding: per(20, $tab);
  }
  h1 {
    width: 90%;
    color: $milk;
    @include fontSet(48,48,0,$tab);
    font-weight: 400;
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
      height: 3px;
      background-color: $milk;
      transition: margin .4s ease,opacity .4s ease,transform .4s ease;
      &:nth-child(1){margin-top: -10px;}
      &:nth-child(3){margin-top: 10px;}
    }
    &.active{
      span{
        &:nth-child(1){margin: 0; transform: rotate(45deg);}
        &:nth-child(2){opacity: 0;}
        &:nth-child(3){margin: 0; transform: rotate(-45deg);}
      }
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
@include tab() {
#header{
  padding: 0;
  .inner{
    width: $tab - 40px;
    margin: 0 auto;
    padding: per(20, $tab) 0;
  }
  h1 {
    @include fontSet(32,32,0,$tab);
  }
  .btn-menu {
    width: 6%;
    span {
      &:nth-child(1){margin-top: -12px;}
      &:nth-child(3){margin-top: 12px;}
    }
  }
}
}
@include pc{
#header{
  padding: 0;
  .inner{
    @include dflex(sb,c);
    width: (1180 / $pc) * 100%;
    max-width: 1180px;
    margin: 0 auto;
    padding: 15px 0;
  }
  h1 {
    width: auto;
    @include fontSet(32,32,0,$pc);
  }
}
}
</style>

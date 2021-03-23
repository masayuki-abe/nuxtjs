<template>
<div>
  <HtmlHeader
    @getHeaderHeight = "headerHeight"
  />
  <HeroImage
    @getVisualHeight = "visualHeight"
    :hHeightPadding="hHeight"
  />
  <div
    id="wrap"
  >
    <Nuxt />
  </div><!--/wrap-->
  <HtmlFooter />
</div>
</template>

<script>
import HtmlHeader from '@/components/organisms/HtmlHeader.vue'
import HeroImage from '@/components/organisms/HeroImage.vue'
import HtmlFooter from '@/components/organisms/HtmlFooter.vue'

export default {
  components: {
    HtmlHeader,
    HeroImage,
    HtmlFooter
  },
  data(){
    return{
      hHeight: '',
      vHeight: ''
      //pageName : this.$route.name
    }
  },
  mounted(){
    //console.log(this.pageName)
  },
  computed:{
    isMobile(){
      return this.wWidth <= 1024;
    }
  },
  methods: {
    headerHeight(headerHeight){
      this.hHeight = headerHeight + 'px'
      console.log(this.hHeight + 'pxxxx')
    },
    visualHeight(visualHeight){
      this.vHeight = visualHeight + 'px'
      console.log(this.vHeight + 'vheight')
    },
  }
}
</script>

<style lang="scss">
body{
  position: relative;
  #wrap{
    position: relative;
    z-index: 100;
    background-color: $milk;
  }
}
</style>
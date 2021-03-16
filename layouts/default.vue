<template>
<div>
  <HtmlHeader
    @getHeaderHeight = "headerHeight"
  />
  <HeroImage
    :hHeightPadding="hHeight"
  />
  <div
    @getVisualHeight = "visualHeight"
    id="wrap"
    :style="{paddingTop: vHeight + 'px'}"
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
      console.log(this.vHeight + 'pxyyy')
    },
  }
}
</script>

<style lang="scss">
body{
  position: relative;
}
</style>
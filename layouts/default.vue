<template>
<div>
<HtmlHeader
  @getHeaderHeight = "headerHeight"
/>
<div
  :style="{paddingTop: hHeight + 'px'}"
  id="wrap"
>
<HeroImage />
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
      hHeight: ''
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
    headerHeight(domHeaderHeight){
      this.hHeight = domHeaderHeight
    }
  }
}
</script>

<style lang="scss">
body{
  position: relative;
}
</style>
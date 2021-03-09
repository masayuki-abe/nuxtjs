<template>
<div>
<HtmlHeader />
<HeroImage />
<div id="wrap">
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
      //pageName : this.$route.name
    }
  },
  mounted(){
    //console.log(this.pageName)
  },
}
</script>

<style lang="scss">
body{
  position: relative;
}
</style>
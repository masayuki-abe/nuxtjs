<template>
<div class="home">
  <section id="box01">
    <div class="common-box">
      <TitSection
        titleTag="h3"
        titleClass="serif"
        titleText='Welcome to a "cafe NORTH FOXES".'
        class="tit-section"
      />
      <p class="txt">イントロダクション</p>
    </div>
  </section><!--/box01-->

  <section id="box02" class="common-box">
    <TitSection
      titleTag="h3"
      titleClass="serif"
      titleText="Pickup!"
      class="tit-section"
    />
    <FrontPickup
      @getPickupTitle = "intoPickupTitle"
    />
  </section><!--/box02-->

  <section id="box03" class="common-box">
    <TitSection
      titleTag="h3"
      titleClass="serif"
      titleText="Blog"
      class="tit-section"
    />
    <ArticleList />
    <BtnRounded
      linkText="もっと見るる"
      linkPath="/blog/"
    />
  </section><!--/box03-->
</div>
</template>

<script>
import ArticleList from '@/components/molecules/ArticleList.vue'
import FrontPickup from '@/components/molecules/FrontPickup.vue'
import BtnRounded from '@/components/atoms/BtnRounded.vue'
import TitSection from '@/components/atoms/TitSection.vue'

export default{
  components: {
    ArticleList,
    FrontPickup,
    BtnRounded,
    TitSection
  },

  data(){
    return{
      pickupTit: ''
    }
  },
  methods: {
    intoPickupTitle(pickupTitle){
      this.PickupTit　= pickupTitle
      console.log(this.PickupTit + 'のさき')
    }
  },
  mounted() {
    this.intoPickupTitle()
  }
}
</script>

<style lang="scss" scoped>
#box01{
  background-color: $smokeBrown;
  color: $milk;
}
</style>
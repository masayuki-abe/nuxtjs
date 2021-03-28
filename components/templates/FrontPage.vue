<template>
<div class="home">
  <section id="box01">
    <div class="common-box">
      <TitSection
        titleTag="h3"
        titleClass="serif"
        titleText='Since 1999.'
        class="tit-section"
      />
      <p class="txt">その時そのときでやりたいことが異なって。<br>
      その度にこのウェブサイトも形を変えているわけですが、名前だけはずっといまのまま。</p>
    <BtnRounded
      linkText="About"
      linkPath="/about/"
    />
    </div>
  </section><!--/box01-->

  <section id="box02">
    <div class="common-box">
      <TitSection
        titleTag="h3"
        titleClass="serif"
        titleText="Blog"
        class="tit-section"
      />
      <FrontPickup
        @getPickupTitle = "intoPickupTitle"
      />
    </div>
  </section><!--/box02-->

  <section id="box03">
      <TitSection
        titleTag="h3"
        titleClass="serif"
        titleText="Reading log"
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
  h3{
    padding: 1em 0 6em;
    color: $milk;
    font-weight: 400;
  }
  .txt{
    padding-bottom: 3em;
    @include fontSet(14,32,300,$tab);
  }
  .btn-rounded{
    @include fontSet(14,14,0,$tab);
  }
}
</style>
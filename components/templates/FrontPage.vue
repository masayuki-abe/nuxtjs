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
        titleText="Message"
        class="tit-section"
      />
      <FrontPickup
        @getPickupTitle = "intoPickupTitle"
      />
    </div>
  </section><!--/box02-->

  <section id="box03">
    <div class="common-box none">
      <TitSection
        titleTag="h3"
        titleClass="serif"
        titleText="Reading log"
        class="tit-section"
      />
    </div>
    <ArticleList />
    <div class="common-box">
      <BtnRounded
        linkText="More"
        linkPath="/blog/"
      />
    </div>
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
    @include fontSet(14,14,300,$tab);
  }
}
@include pc() {
#box01{
  h3{
    padding: 1em 0 6em;
    color: $milk;
    font-weight: 400;
  }
  .txt{
    padding-bottom: 3em;
    @include fontSet(14,32,300,$pc);
  }
  .btn-rounded{
    @include fontSet(14,14,300,$pc);
  }
}
}


#box02{
  background-color: $white;
  border-bottom: 1px $darkBrown solid;
  .common-box{
    padding: per(60,$tab) 0 per(30,$tab);
    h3{
      @include ta(center);
    }
  }
}
@include pc() {
#box02{
  .common-box{
    padding: per(60,$pc) 0 per(30,$pc);
  }
}
}



#box03{
  .common-box{
    padding: per(60,$tab) 0;
    h3{@include ta(center);}
    .btn-rounded{
      @include fontSet(32,32,300,$tab);
    }
  }
}
@include lap() {
#box03{
  .common-box{
    padding: per(60,$lap) 0;
    .btn-rounded{
      @include fontSetPC(20,20,300);
    }
  }
}
}
</style>
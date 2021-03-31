<template>
<footer id="footer">
  <dl>
    <SiteName
      htmlTag="flogo"
    />
    <dd
      class="common-box"
    >
      <NaviBody
        role="Fnavi"
      />
    </dd>
  </dl>
  <aside class="copyright">&copy;2021 cafe NORTH FOXES</aside>
  <BtnSclTop />
</footer>
</template>

<script>
import SiteName from '@/components/atoms/SiteName.vue';
import NaviBody from '@/components/molecules/NaviBody.vue';
import BtnSclTop from '@/components/atoms/BtnSclTop.vue';

export default {
  components: {
    SiteName,
    NaviBody,
    BtnSclTop,
  }
}
</script>

<style lang="scss" scoped>
#footer{
  position: relative;
  z-index: 100;
  background-color: $beige;
  dl{
    dt{
      padding: 1em 0;
      color: $darkBrown;
      @include fontSet(48,48,100,$tab);
      @include ta(center);
    }
  }
  .copyright{
    padding-bottom: 2em;
    @include fontSet(24,24,0,$tab);
    @include ta(center);
  }
}
@include lap() {
#footer{
  dl{
    dt{
      @include fontSetPC(24,24,100);
    }
  }
  .copyright{
    padding-bottom: 5em;
    @include fontSetPC(12,12,0);
  }
}
}
</style>

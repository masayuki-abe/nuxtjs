<template>
<footer>
<dl>
<SiteName htmlTag="flogo" />
<dd><NaviBody role="Fnavi" /></dd>
</dl>
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
  background-color: $beige;
}
</style>

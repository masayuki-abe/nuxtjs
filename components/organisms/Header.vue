<template>
<header id="header" class="py-3"><div class="container d-flex justify-content-between align-items-center bg-light p-4">
<SiteName htmlTag="h1" />
<BtnMenu />
<Navi Role="Gnavi" />
</div> </header><!--/header-->
</template>

<script>
import BtnMenu from '@/components/atoms/BtnMenu.vue';
import SiteName from '@/components/atoms/SiteName.vue';
import Navi from '@/components/atoms/Navi.vue';

export default {
  components: {
    SiteName,
    BtnMenu,
    Navi,
  }
}
</script>

<template>
<footer>
<dl>
<SiteName htmlTag="dt" />
<dd><Navi Role="Fnavi" /></dd>
</dl> 
</footer>
</template>

<script>
import SiteName from '@/components/atoms/SiteName.vue';
import Navi from '@/components/atoms/Navi.vue';

export default {
  components: {
    SiteName,
    Navi,
  }
}
</script>

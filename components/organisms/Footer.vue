<template>
<footer>
<dl>
<dt><SiteName /></dt>
<dd><nav class="fnavi">
<Navi />
</nav></dd>
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

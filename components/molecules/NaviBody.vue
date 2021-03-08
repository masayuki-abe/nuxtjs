<template>
<nav v-if="role == 'Gnavi'" class="gnavi">
<NaviList
  v-on:changeStatus="closeSpGnavi()"
/>
</nav>
<nav v-else-if="role == 'Fnavi'" class="fnavi">
<NaviList />
</nav>
</template>

<script>
import NaviList from '@/components/atoms/NaviList.vue';

export default {
  components: {
    NaviList,
  },
  props: {
    role:{
      type: String
    },
  },
  methods: {
    closeSpGnavi() {
      this.$emit('toHtmlHeader')
    },
  }
}
</script>

<style lang="scss" scope>
nav{
  &.gnavi{
    position: absolute;
    left: 0;
    top: 100%;
    width: 100%;
    background-color: rgba(0,0,0,.8);
  }
}

</style>
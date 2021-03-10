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

<style lang="scss" scoped>
nav{
  &.gnavi{
    position: absolute;
    left: 0;
    top: 100%;
    width: 100%;
    background-color: rgba(255,255,255,.8);
    ul{
      list-style: none;
      li{
        a{color: #333;}
      }
    }
  }
}
@include lap() {
nav {
  &.gnavi{
    position: static;
  }
}
}
</style>
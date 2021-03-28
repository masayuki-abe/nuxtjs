<template>
<p class="btn-rounded">
  <nuxt-link
    :to="linkPath"
  >
    <span>{{linkText}}</span>
  </nuxt-link>
</p>
</template>

<script>
export default {
  props: {
    linkText: {
      type: String
    },
    linkPath: {
      type: String
    }
  }
}
</script>

<style lang="scss">
.btn-rounded{
  @include fontSet(32,32,0,$tab);
  @include ta(right);
  a{
    position: relative;
    width: 100%;
    &:after{
      content: "";
      position: absolute;
      left: 0;
      top: 0;
      width: 100%;
      height: 50%;
      background-color: $brown;
      transform: translateX(.5em) translateY(.8em);
    }
    span{
      position: relative;
      z-index: 2;
    }
  }
}
</style>
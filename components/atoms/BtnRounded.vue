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
@include pc() {
.btn-rounded{
  @include fontSet(16,16,0,$pc);
  a{
    &:after{
      content: "";
      opacity: 1;
      position: absolute;
      left: 0;
      top: 0;
      width: 100%;
      height: 50%;
      background-color: $brown;
      transform: translateX(.5em) translateY(.8em);
      transition: opacity .6s ease, transform .8s ease;
    }
    &:hover{
      &:after{
        opacity: 0;
        transform: translateX(3em) translateY(.8em);
      }
    }
    span{
      position: relative;
      z-index: 2;
    }
  }
}
}
</style>
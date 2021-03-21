<template>
  <component
    :is="titleTag"
    :class="titleClass"
  >
    {{titleText}}
  </component>
</template>

<script>
export default {
  props: {
    titleTag: {
      type: String
    },
    titleClass: {
      type: String
    },
    titleText: {
      type: String
    }
  }
}
</script>

<style lang="scss" scoped>
.tit-section{
  padding-bottom: .2em;
  color: $lightBrown;
  @include fontSet(48,56,100,$tab)
}
@include tab() {
.tit-section{
  padding-bottom: .2em;
  color: $lightBrown;
  @include fontSet(32,48,100,$tab)
}
}
</style>
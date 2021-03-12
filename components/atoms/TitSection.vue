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
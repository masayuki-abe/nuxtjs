<template>
<p class="btn-rounded">
  <nuxt-link
    :to="linkPath"
  >
    {{linkText}}
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
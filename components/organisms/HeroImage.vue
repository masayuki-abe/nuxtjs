<template>
<section 
  v-if="this.$route.name === 'index'"
  id="visual"
  class="index"
>
<h1>{{title}}</h1>
</section>
<section 
  v-else
  id="visual"
  class="lower"
>
<h1>Page title</h1>
</section>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: ''
    }
  },
  data(){
    return{
    }
  }
}
</script>


<template>
<section 
  v-if="this.$route.name === 'index'"
  id="visual"
  class="index"
>
<h1>{{this.$route.name}}</h1>
</section>
<section 
  v-else
  id="visual"
  class="lower"
>
<h1>{{this.$route.name}}</h1>
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

<style lang="scss">
#visual{
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 200px;
  background-color: #333;
  color: #fff;
  &.lower{
    height: 100px;
    background-color: #ccc;
    color: #333;
  }
}
</style>


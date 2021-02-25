<template>
<aside class="btn-menu col-1" @click='btnActive=!btnActive' :class='{active:btnActive}'>
  <span></span>
  <span></span>
  <span></span>
</aside>
</template>

<script>
export default {
  data(){
    return{
      btnActive: false
    }
  }
}
</script>

<style lang="scss">
.btn-menu{
  span{display: inline-block; width: 100%; height: 2px; background-color: #333;}
}
</style>
<template>
<section id="box01">
<ArticleList />
</section><!--/box01-->
</template>

<script>
import ArticleList from '@/components/molecules/ArticleList.vue'

export default{
  components: {
    ArticleList
  },
  head() {
    return {
      title: 'Blog｜cafe NORTHFOXES',
    }
  },
  data(){
    return{
      pageTitle: 'Blog Page Title'
    }
  },
}
</script>

<style lang="scss" scoped>
#box01{
  padding: per(100,$tab) 0;
}
</style>
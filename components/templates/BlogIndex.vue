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
      title: 'Blogページ',
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
  width: per($tab - 60, $tab);
  margin: 0 auto;
  padding: per(100,$tab) 0;
}
</style>
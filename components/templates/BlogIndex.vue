<template>
<section id="box01">
<p v-if="this.$route.name === 'blog'">blog index<br>{{pageTitle}}</p>
<p v-else-if="this.$route.name === 'blog-category'">blog category<br>{{pageTitle}}</p>
<ArticleList />
</section><!--/box01-->
</template>

<script>
import ArticleList from '@/components/atoms/ArticleList.vue'

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
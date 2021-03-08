<template>
<section id="box01">
<p>test</p>
<ArticleList roopCount="3" />
</section><!--/box01-->
</template>

<script>
import ArticleList from '@/components/atoms/ArticleList.vue'

export default{
  components: {
    ArticleList
  },

  data(){
    return{
    }
  },
}
</script>
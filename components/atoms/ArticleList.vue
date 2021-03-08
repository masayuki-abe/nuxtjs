<template>
<section class="article-list">
<ul class="list-unstyled">
<li
  v-for="article in limitCount"
  :key='article.date'
>
  <dl>
    <dt>{{article.date}}</dt>
    <dd>{{article.title}}</dd>
  </dl>
  <article>{{article.contents}}</article>
</li>
</ul>
</section><!--/articlelist-->
</template>

<script>
export default {
  data(){
    return{
      articles: [
        {
          date: '2021/03/08',
          title: 'test article',
          contents: 'これはテストです。これはテストです。これはテストです。'
        },
        {
          date: '2021/03/07',
          title: 'test article2',
          contents: 'これはテスト2です。これはテストです。これはテストです。'
        },
        {
          date: '2021/03/06',
          title: 'test article3',
          contents: 'これはテスト3です。これはテストです。これはテストです。'
        },
        {
          date: '2021/03/05',
          title: 'test article4',
          contents: 'これはテスト4です。これはテストです。これはテストです。'
        },
        {
          date: '2021/03/04',
          title: 'test article5',
          contents: 'これはテスト5です。これはテストです。これはテストです。'
        }
      ]
    }
  },
  computed: {
    limitCount() {
      if(this.$route.name === 'index'){
        return this.articles.slice(0,3)
      }else{
        return this.articles
      }
    }
  }
}
</script>
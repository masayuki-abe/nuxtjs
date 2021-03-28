<template>
<article class="article-list">
<ul class="list-unstyled">
<li
  v-for="(article, index) in limitCount"
  :key='article.date'
>
  <dl>
    <dt><img :src="'http://books.google.com/books/content?id=' + article.id + '&printsec=frontcover&img=1&zoom=5&edge=curl&source=gbs_api'">
</dt>
    <dd>{{article.title}}</dd>
  </dl>
  <p
    v-html="article.intro"
  />
  <p
    class="btn-readmore"
    :class="{'is-active': isOpen[index]}"
    @click="handleToggle(index)"
  >
    続きを読む
  </p>
  <transition
    name="acoBody"
    @before-enter="beforeEnter"
    @enter="enter"
    @before-leave="beforeLeave"
    @leave="leave"
  >
    <article
      v-show="isOpen[index]"
      class="aco-body"
    >


      <p
        v-for="articleText in article.contents"
        :key='articleText.id'
        v-html="articleText"
      />
    </article>
  </transition>
</li>
</ul>
</article><!--/articlelist-->
</template>

<script>
import axios from 'axios'

export default {
  data(){
    return{
      isOpen: [],
      posts: [],
    }
  },
  computed: {
    limitCount() {
      if(this.$route.name === 'index'){
        return this.articles.slice(0,3)
      }else{
        return this.articles
      }
    },
    articles() {
      const data = [
        {
          id: 'vpCBDwAAQBAJ',
          date: '2021/03/08',
          title: '『殺人者の顔』<span>ヘニング・マンケル</span>',
          intro: 'ここにイントロダクションが入ります。<br>これはイントロダクションです。',
          contents: [
            'これはテストです。<br>これはテストです。これはテストです。',
            'これはテスト2です。これはテスト2です。これはテスト2です。'
          ]
        },
        {
          date: '2021/03/07',
          title: 'test article2',
          intro: 'イントロダクション',
          isbn: '4150412677',
          contents: [
            'これはテストXです。これはテストです。これはテストです。'
          ]
        },
        {
          date: '2021/03/06',
          title: 'test article3',
          contents: [
            'これはテスト3です。これはテストです。これはテストです。'
          ]
        },
        {
          date: '2021/03/05',
          title: 'test article4',
          contents: [
            'これはテスト4です。これはテストです。これはテストです。'

          ]
        },
        {
          date: '2021/03/04',
          title: 'test article5',
          contents: [
            'これはテスト5です。これはテストです。これはテストです。'
          ]
        }
      ]
      return data
    }
  },
  created() {
    //アコーディオンの数だけ開閉フラグを作成
    this.isOpen = Array(this.articles.length).fill(false)
  },
  methods: {
    //メニューを開閉する
    handleToggle(index) {
      this.isOpen.splice(index, 1, !this.isOpen[index])
    },
    //スライド開閉要素の高さを取得
    beforeEnter(el) {
      el.style.height = '0'
    },
    enter(el) {
      el.style.height = el.scrollHeight + 'px'
    },
    beforeLeave(el) {
      el.style.height = el.scrollHeight + 'px'
    },
    leave(el) {
      el.style.height = '0'
    }
  },
  mounted() {
    axios.get('https://www.googleapis.com/books/v1/users/108445538797584670491/bookshelves/1001/volumes')
    // axios.get('https://www.googleapis.com/books/v1/volumes?q=isbn:4488209025')
    //axios.get('https://jsonplaceholder.typicode.com/posts')
    .then((response) => this.posts = response.data.items)
  }
}
</script>

<style lang="scss">
.aco-body {
  transition: height .4s ease-in-out;
  overflow: hidden;
  p{
    @include fontSet(32, 48, 300, $tab);
  }
}
@include tab(){
.aco-body{
  p{
    @include fontSet(16, 24, 500, $tab);
  }
}
}
</style>
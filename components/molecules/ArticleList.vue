<template>
<article class="article-list">
<ul class="list-unstyled">
<li
  v-for="(article, index) in limitCount"
  :key='article.date'
>
  <dl>
    <dt><img :src="'http://books.google.com/books/content?id=' + article.id + '&printsec=frontcover&img=1&zoom=5&edge=curl&source=gbs_api'" :alt="article.title"></dt>
    <dd>{{article.title}}<span>{{article.author}}</span></dd>
  </dl>
  <p
    class="btn-readmore"
    :class="{'is-active': isOpen[index]}"
    @click="handleToggle(index)"
  >
    ＋
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
export default {
  data(){
    return{
      isOpen: [],
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
          id: 'Prj-h8CftAMC',
          title: '『ライ麦畑でつかまえて』',
          author: 'J.D. サリンジャー',
          contents: [
            'これはテストです。<br>これはテストです。これはテストです。',
            'これはテスト2です。これはテスト2です。これはテスト2です。'
          ]
        },
        {
          id: '2SdzBQAAQBAJ',
          title: '『星を継ぐもの』',
          author: 'ジェイムズ・P・ホーガン',
          contents: [
            'これはテストです。<br>これはテストです。これはテストです。',
            'これはテスト2です。これはテスト2です。これはテスト2です。'
          ]
        },
        {
          id: 'oRqctQEACAAJ',
          title: '『コールド・コールド・グラウンド』',
          author: 'エイドリアン・マッキンティ',
          contents: [
            'これはテストです。<br>これはテストです。これはテストです。',
            'これはテスト2です。これはテスト2です。これはテスト2です。'
          ]
        },
        {
          id: 'Jo_ZAwAAQBAJ',
          title: '『戦士志願』',
          author: 'ロイス・マクマスター・ビジョルド',
          contents: [
            'これはテストです。<br>これはテストです。これはテストです。',
            'これはテスト2です。これはテスト2です。これはテスト2です。'
          ]
        },
        {
          id: '2CiRMQEACAAJ',
          title: '『暗殺者グレイマン』',
          author: 'マーク・グリーニー',
          contents: [
            'これはテストです。<br>これはテストです。これはテストです。',
            'これはテスト2です。これはテスト2です。これはテスト2です。'
          ]
        },
        {
          id: 'vpCBDwAAQBAJ',
          title: '『殺人者の顔』',
          author: 'ヘニング・マンケル',
          contents: [
            'これはテストです。<br>これはテストです。これはテストです。',
            'これはテスト2です。これはテスト2です。これはテスト2です。'
          ]
        },
      ]
      return data
    },
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
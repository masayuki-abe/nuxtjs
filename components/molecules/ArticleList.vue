<template>
<div class="article-list">
<ul>
<li
  v-for="(article, index) in limitCount"
  :key='article.date'
>
  <dl class="common-box">
    <dt><img :src="'http://books.google.com/books/content?id=' + article.id + '&printsec=frontcover&img=1&zoom=5&edge=curl&source=gbs_api'" :alt="article.title"></dt>
    <dd><span class="book-title">{{article.title}}</span><span class="book-author">{{article.author}}</span></dd>
  </dl>
  <p
    class="btn-readmore common-box none"
    :class="{'is-active': isOpen[index]}"
    @click="handleToggle(index)"
  >
    <span></span>
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
      class="aco-body common-box"
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
</div><!--/articlelist-->
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
          id: 'Ky-zPAAACAAJ',
          title: '『ライ麦畑でつかまえて』',
          author: 'J.D. サリンジャー',
          contents: [
            'ホールデン・コールフィールドに出会っていなかったら人生どうなっていただろうか？　と考えることは？',
            'いまでも自分は、ライ麦畑のキャッチャーになりたいし、ならなくちゃいけないと思っている。',
            '村上訳より野崎訳派です。',
          ]
        },
        {
          id: '2SdzBQAAQBAJ',
          title: '『星を継ぐもの』',
          author: 'ジェイムズ・P・ホーガン',
          contents: [
            'ドキドキです。最後までドキドキなんです。そしてワクワクするんです。',
            'これがSFというのであれば、SFってなんて楽しいんだろう！　と思うこと間違いなしの1冊。',
            'ホーガンの世界ってかなり当たり外れあると思っていますが、本作については文句のつけようなし、です。',
          ]
        },
        {
          id: 'oRqctQEACAAJ',
          title: '『コールド・コールド・グラウンド』',
          author: 'エイドリアン・マッキンティ',
          contents: [
            'テロが盛んだった時代のアイルランドを肌で感じられる警察小説。',
            'ストーリやキャラクタもさることながら、この本のもっと素晴らしいところは翻訳。言葉の選択が秀逸。賛否両論ですが、「これが翻訳だ！」と思います。'
          ]
        },
        {
          id: 'Jo_ZAwAAQBAJ',
          title: '『戦士志願』',
          author: 'ロイス・マクマスター・ビジョルド',
          contents: [
            'マイルズ・ヴォルコシガンの記念すべき1作目。本作を読んだ人はこれから長いながい旅をマイルズとともにするわけです。（『女提督コーデリア』を除外すればシリーズ最終巻は『マイルズの旅路』）',
            'マイルズというキャラクタがとにかく魅力的。非常によく作られたキャラクタだと思います。',
            'ビジョルドは五神教シリーズを代表とするファンタジィの名手でもあって、「天才じゃないか」と思わせる作家の一人です。',
          ]
        },
        {
          id: '2CiRMQEACAAJ',
          title: '『暗殺者グレイマン』',
          author: 'マーク・グリーニー',
          contents: [
            '憧れの強い男を一人選べ、と問われた場合、ジェイソン・ステイサムやブルース・ウィルスともう一人、グレイマンことコート・ジェントリーのうち誰を選ぶか迷います。',
            'まるで映像を見ているような小説で、マット・デイモンの「ボーン・シリーズ」を思い浮かべた人も多いのではないかな、と。',
            '強いだけではなく自身の正義を貫こうとする。それがコート・ジェントリーです。'
          ]
        },
        {
          id: 'vpCBDwAAQBAJ',
          title: '『殺人者の顔』',
          author: 'ヘニング・マンケル',
          contents: [
            'いつだってヴァランダーのように仕事に取り組みたい、と思います。（そのせいで彼の家庭はめちゃくちゃになったかもしれないけれど）',
            'クルト・ヴァランダーは人生の師であり、いつかは追いつきたい目標です。',
            '彼の人生（物語）は終わっていますが、それでもやはり、ヘニング・マンケルが生きていれば！　と思わずにはいられません。'
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
.article-list{
  ul{
    list-style: none;
    li{
      margin-bottom: per(60,$tab);
      padding-bottom: per(60,$tab);
      border-bottom: 1px $darkBrown solid;
      &:last-child{
        margin-bottom: 0;
        padding-bottom: 0;
        border-bottom: none;
      }
      dl{
        padding-bottom: per(120,$tab);
        dt{
          width: 70%;
          margin: 0 auto per(40,$tab);
          img{
            width: 100%;
          }
        }
        dd{
          .book-title{
            @include dis(block); padding-bottom: 1em; @include fontSet(32,48,100,$tab); font-weight: 700; @include ta(center);
          }
          .book-author{
            @include dis(block); @include fontSet(28,28,100,$tab); font-style: italic; @include ta(right);
            &:before{
              content: "－"; margin-right: .5em;
            }
          }
        }
      }
      .btn-readmore{
        @include dflex(fe,c);
        span{
          @include dis(inline-block);
          width: 1em;
          height: 1em;
          border-right: 2px $darkBrown solid;
          border-bottom: 2px $darkBrown solid;
          @include fontSet(32,32,0,$tab);
          transform: rotate(-45deg);
          transition: transform .4s ease;
        }
        &.is-active{
          span{
            transform: rotate(405deg);
          }
        }
      }
    }
  }
}
.aco-body {
  transition: height .4s ease-in-out;
  overflow: hidden;
  padding-top: per(60,$tab);
  p{
    @include fontSet(32, 48, 300, $tab);
  }
}
@include tab(){
.article-list{
  ul{
    li{
      margin-bottom: per(60,$tab);
      padding-bottom: per(60,$tab);
      dl{
        padding-bottom: per(120,$tab);
        dt{
          width: 45%;
          margin: 0 auto per(30,$tab);
        }
        dd{
          .book-title{
            padding-bottom: .5em; @include fontSet(32,48,100,$tab); font-weight: 700; @include ta(center);
          }
        }
      }
    }
  }
}
}
@include lap() {
.article-list{
  ul{
    @include dflex(c,st);
    li{width: 33%;
      margin: 0 3% 30px 0;
      padding: per(20,$lap);
      border: 1px $darkBrown solid;
      &:last-child{
        margin: 0 3% 30px 0;
        padding: per(20,$lap);
        border-bottom: 1px $darkBrown solid;
      }
      dl{
        width: 100%;
        padding-bottom: per(20,$lap);
        dt{
          width: 70%;
          margin: 0 auto per(20,$lap);
        }
        dd{
          .book-title{
            padding-bottom: .5em;
            @include fontSetPC(16,24,100);
          }
          .book-author{
            @include fontSetPC(14,14,100);
            @include ta(center);
            &:before{
              content: none;
            }
          }
        }
      }
      .btn-readmore{
        @include dflex(fe,c);
        span{
          @include dis(inline-block);
          width: 1em;
          height: 1em;
          @include fontSetPC(16,16,0);
          transform: rotate(-45deg) translateX(.5em);
          transition: transform .4s ease;
        }
        &.is-active{
          span{
            transform: rotate(405deg);
          }
        }
      }
    }
  }
}
.aco-body {
  transition: height .4s ease-in-out;
  overflow: hidden;
  padding-top: per(40,$lap);
  p{
    @include fontSetPC(16,24,300);
  }
}
}
@include pc() {
.article-list{
  ul{
    @include dflex(sb,st);
    width: per($pc - 40, $pc);
    max-width: 1180px;
    margin: 0 auto;
    li{width: 32%;
      margin: 0 0 30px 0;
      &:last-child{
        margin: 0 0 30px 0;
      }
    }
  }
}
}
</style>
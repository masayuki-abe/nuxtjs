<template>
<div class="front-pickup">
  <dl>
    <dt
      @click="openModal"
      class="txt"
    >
      {{pickupTitle}}
    </dt>
    <dd class="modal">
      <Modal
        v-if="modalFlag"
        @close-modal="closeModal"
      >
        <h4 class="serif">{{pickupTitle}}</h4>
        <p>4年ぶり？　にウェブサイトをリニュアルした。</p>
        <p>今まではWordPressで構築していたけれど、Vue.jsやNuxt.js、アトミックデザインといった考え方を勉強するために、まかりなりにもNuxt.jsを採用。</p>
        <p>JavaScriptが難しすぎる。いままでJS書いてこなかったツケがここにきて完全にまわってきた感じ。CSSでどうにかできることはCSSで！　という考えに固執してきたし、それはそれで間違いではないと思うけれど、それをJSを勉強しないイイワケにしていたんですよね、と。</p>
        <p>Nuxt.jsを使ってみた所感としては、いろいろおもしろい。特にtransitionとか。優秀だなーと思います。Larabelで？　APIとか？　Firabase？？？　そういう次元じゃないんですが、触ってみて面白いと感じられたのは良かった。歳を取っても何かを学ぶのは楽しい。</p>
        <p>アトミックデザインっていう考え方にはいろいろ思うところがある。というか、これが一番難しいと感じる一方でやりがいを感じてる。今回はたかだか3ページだからいいけれど、中～大規模サイトでアトミックデザインを採用した場合、最初の設計間違えたらとんでもないことになりそう。</p>
        <p>そういった修正にも容易に対応できますよーというものだと思うけれど、「うん、そうだよね！」と納得できるほど知識と経験が追いついていない。でも突然のデザイン・仕様変更にも柔軟に対応できる初期設計を行うっていうところに燃える。これは必ずモノにしたい。</p>
        <p>あ、コンテンツは減らしました。正直、個人サイトでやりたいことって実はあまりない。読書の感想にしても自作の小説にしても、公開できる場所が山のようにある。個人サイトでやる必要性がないよなぁ。</p>
        <p>いまはBBSもなければCGIのチャットもない。でも「cafe NORTH FOXES」は捨てられない。リニュアルする度に高校生からの思い出がよみがえる。</p>
      </Modal>
    </dd>
  </dl>
</div>
</template>

<script>
import Modal from '@/components/atoms/ModalBase.vue'

export default {
  components: {
    Modal,
  },

  data(){
    return{
      modalFlag: false,
      pickupTitle: "ウェブサイトリニュアル"
    }
  },
  methods: {
    openModal() {
      this.modalFlag = true
    },
    closeModal() {
      this.modalFlag = false
    }
  }
}
</script>

<style lang="scss" scoped>
.front-pickup{
  dl{
    dt{
      position: relative;
      padding-bottom: 3em;
      @include ta(center);
      &:after{
        content: "＋";
        position: absolute;
        right: 0;
        bottom: 0;
      }
    }
    dd{
      h4{
        color: $lightBrown;
        @include fontSet(48,52,100,$tab);
        font-weight: 400;
      }
    }
  }
}
@include lap(){
.front-pickup{
  dl{
    dt{
      &:after{
        opacity: 0;
        content: "＋";
        position: absolute;
        right: 50%;
        bottom: 0;
        transform: translateX(50%);
        transition: opacity .4s ease;
      }
      &:hover{
        cursor: pointer;
        &:after{
          opacity: 1;
        }
      }
    }
    dd{
      h4{
        color: $lightBrown;
        @include fontSetPC(32,48,100);
        font-weight: 400;
      }
    }
  }
}
}

</style>
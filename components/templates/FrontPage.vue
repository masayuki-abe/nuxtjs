<template>
<div class="home">
<section id="box01">
  <h3>Introduction</h3>
  <p>イントロダクション</p>

</section><!--/box01-->

<section id="box02">
  <h3>Pickup!</h3>
  <dl>
    <dt @click="openModal">ピックアップのタイトル</dt>
    <dd class="modal">
      <Modal v-if="modalFlag" @close-modal="closeModal">
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
        <aside @click="closeModal">閉じる</aside>
      </Modal>
    </dd>
  </dl>
</section><!--/box02-->

<section id="box03">
  <h3>Blog</h3>
  <ArticleList />
</section><!--/box03-->
</div>
</template>

<script>
import ArticleList from '@/components/atoms/ArticleList.vue'
import Modal from '@/components/atoms/ModalBase.vue'

export default{
  components: {
    ArticleList,
    Modal
  },

  data(){
    return{
      modalFlag: false,
    }
  },
  methods: {
    openModal() {
      this.modalFlag = true
    },
    closeModal() {
      this.modalFlag = false
    },
  }
}
</script>
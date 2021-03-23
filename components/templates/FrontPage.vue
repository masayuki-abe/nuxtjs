<template>
<div class="home">
  <section id="box01" class="common-box">
    <TitSection
      titleTag="h3"
      titleClass="serif"
      titleText="Introduction"
      class="tit-section"
    />
    <p>イントロダクション</p>
  </section><!--/box01-->

  <section id="box02" class="common-box">
    <TitSection
      titleTag="h3"
      titleClass="serif"
      titleText="Pickup!"
      class="tit-section"
    />
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
        </Modal>
      </dd>
    </dl>
  </section><!--/box02-->

  <section id="box03" class="common-box">
    <TitSection
      titleTag="h3"
      titleClass="serif"
      titleText="Blog"
      class="tit-section"
    />
    <ArticleList />
    <BtnRounded
      linkText="もっと見るる"
      linkPath="/blog/"
    />
  </section><!--/box03-->
</div>
</template>

<script>
import ArticleList from '@/components/molecules/ArticleList.vue'
import Modal from '@/components/atoms/ModalBase.vue'
import BtnRounded from '@/components/atoms/BtnRounded.vue'
import TitSection from '@/components/atoms/TitSection.vue'

export default{
  components: {
    ArticleList,
    Modal,
    BtnRounded,
    TitSection
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
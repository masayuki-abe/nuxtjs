<template>
<div class="front-pickup">
  <dl>
    <dt @click="openModal">{{pickupTitle}}</dt>
    <dd class="modal">
      <Modal v-if="modalFlag" @close-modal="closeModal">
        <h4>{{pickupTitle}}</h4>
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
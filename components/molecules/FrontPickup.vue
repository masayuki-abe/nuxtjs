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
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。</p>
        <p>ここにモーダルの内容が入ります。ここに内容が入ります。</p>
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
@include pc(){
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
        @include fontSet(48,52,100,$tab);
        font-weight: 400;
      }
    }
  }
}
}

</style>
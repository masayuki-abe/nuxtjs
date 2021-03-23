<template>
<transition
  name="modal"
  appear
>
  <div class="modal-wrap" @click="closeModal">
    <div class="modal-window">
      <div class="modal-content">
        <slot />
      </div>
    </div>
  </div>
</transition>
</template>

<script>
export default {
  methods: {
    closeModal() {
      this.$emit('close-modal')
    }
  }
}
</script>

<style lang="scss" scoped>
.modal {
  .modal-wrap {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    z-index: 9999;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,.7);
    .modal-window{
      width: 70%;
      height: 80%;
      background-color: rgba(255,255,255,.9);
      .modal-content{
        padding: 20px;
      }
    }
  }
}
.modal-enter-active,
.modal-leave-active {
  transition: opacity .4s ease;
  .modal-window {
    transition: opacity .4s, transform ,4s;
  }
}
.modal-leave-active {
  transition: opacity .6s ease .4s;
}
.modal-enter,
.modal-leave-to {
  opacity: 0;
  .modal-window{
    opacity: 0;
    transform: translateY(-20px);
  }
}
</style>
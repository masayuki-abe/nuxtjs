<template>
<transition
  name="modal"
  appear
>
  <div
    class="modal-wrap"
    @click="closeModal"
  >
    <div class="modal-window">
      <span
        @click="closeModal"
        class="btn-close"
      >
      </span>
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

<style lang="scss">
.modal {
  .modal-wrap {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,.7);
    .modal-window{
      position: relative;
      width: 90%;
      height: 75%;
      background-color: rgba($milk,.9);
      .btn-close{
        @include dis(inline-block);
        position: absolute;
        right: 0;
        top: -25px;
        width: 20px;
        height: 20px;
        &:before,&:after{
          content: "";
          position: absolute;
          top: 0;
          left: 50%;
          width: 3px;
          height: 100%;
          background-color: $milk;
        }
        &:before{
          transform: rotate(45deg);
        }
        &:after{
          transform: rotate(-45deg);
        }
      }
      .modal-content{
        position: relative;
        height: 100%;
        overflow-y: scroll;
        padding: 20px;
        @include fontSet(32,48,100,$tab);
        *{
          padding-bottom: 1em;
          &:last-child{
            padding-bottom: 0;
          }
        }
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
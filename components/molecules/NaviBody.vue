<template>
<nav v-if="role == 'Gnavi'" class="gnavi">
<NaviList
  v-on:changeStatus="closeSpGnavi()"
/>
</nav>
<nav v-else-if="role == 'Fnavi'" class="fnavi">
<NaviList />
</nav>
</template>

<script>
import NaviList from '@/components/atoms/NaviList.vue';

export default {
  components: {
    NaviList,
  },
  props: {
    role:{
      type: String
    },
  },
  methods: {
    closeSpGnavi() {
      this.$emit('toHtmlHeader')
    },
  }
}
</script>

<style lang="scss">
nav{
  &.gnavi{
    position: absolute;
    left: 0;
    top: 100%;
    width: 100%;
    background-color: rgba($milk,.9);
    ul{
      list-style: none;
      li{
        @include fontSet(32,32,0,$tab);
        a{
          @include dis(block);
          padding: 1.5em 1em;
          border-bottom: 1px  $darkBrown solid;
          color: $darkBrown;
          @include ta(center);
          &.current{
            background-color: $brown;
            color: $milk;
          }
        }
      }
    }
  }
}
@include tab() {
nav{
  &.gnavi{
    ul{
      @include dflex;
      li{flex-grow: 1;
        @include fontSet(32,32,0,$tab);
        a{
          padding: .5em 1em;
          border-bottom: none;
          border-right: 1px  $darkBrown solid;
          &:last-child{
            border-right: none;
          }
          &.current{
            background-color: $brown;
            color: $milk;
          }
        }
      }
    }
  }
}
}
@include lap() {
nav{
  &.gnavi{
    position: relative;
    width: auto;
    background-color: transparent;
    ul{
      position: static;
      li{
        padding: 0 2em;
        @include fontSet(16,16,0,$pc);
        a{
          position: relative;
          padding: 0 0 .5em;
          border-bottom: none;
          border-right: none;
          color: $milk;
          &:after{
            content: "";
            opacity: 0;
            position: absolute;
            left: 0;
            bottom: 0;
            width: 100%;
            height: 2px;
            background-color: $lightBrown;
            transition: opacity .4s ease;
          }
          &:hover{
            &:after{
              opacity: 1;
            }
          }
          &.current{
            background-color: transparent;
            &:after{
              opacity: 1;
            }
          }
        }
      }
    }
  }
}
}
</style>
<template>
<ul class="list-unstyled">
<li
  v-for="list in lists"
  :key='list.id'
  :class='list.dir'
>
<nuxt-link
  :to='list.path'
  active-class="current"
  @click.native="btnMenuSwitch();"
>
{{list.name}}
</nuxt-link>
</li>
</ul>
</template>

<script>
export default {
  data(){
    return{
      lists: [
        {path: '/', dir: 'home', name: 'HOME'},
        {path: '/about/', dir: 'about', name: 'ABOUT'},
        {path: '/blog/', dir: 'blog', name: 'BLOG'},
      ]
    }
  },
  methods: {
    btnMenuSwitch() {
      this.$emit('changeStatus')
    },
  },
}
</script>
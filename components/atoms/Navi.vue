<template>
<ul class="list-unstyled">
<li v-for='list in lists' :key='list.id' :class='list.dir'><NuxtLink :to='list.path'>{{list.name}}</NuxtLink></li>
</ul>
</template>

<script>
export default {
  data(){
    return{
      lists:[
        {path: '/', dir: 'home', name: 'HOME'},
        {path: '/about/', dir: 'about', name: 'ABOUT'},
        {path: '/blog/', dir: 'blog', name: 'BLOG'},
      ]
    }
  }
}
</script>
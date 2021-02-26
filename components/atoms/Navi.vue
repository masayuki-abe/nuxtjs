<template>
<nav v-if="Role == 'Gnavi'" class="gnavi">
<ul class="list-unstyled">
<li v-for='list in lists' :key='list.id' :class='list.dir'><NuxtLink :to='list.path'>{{list.name}}</NuxtLink></li>
</ul>
</nav>
<nav v-else-if="Role == 'Fnavi'" class="fnavi">
<ul class="list-unstyled">
<li v-for='list in lists' :key='list.id' :class='list.dir'><NuxtLink :to='list.path'>{{list.name}}</NuxtLink></li>
</ul>
</nav>
</template>

<script>
export default {
  Role: 'Navi',
  props:{
    Role: String,
  },
  data(){
    let lists = [
      {path: '/', dir: 'home', name: 'HOME'},
      {path: '/about/', dir: 'about', name: 'ABOUT'},
      {path: '/blog/', dir: 'blog', name: 'BLOG'},
    ];
    return{
      lists
    }
  },
}
</script>
<template>
<h1
  v-if="htmlTag == 'hlogo'"
  class="serif"
>
  <nuxt-link to='/'>
    <span>{{Name}}</span>
  </nuxt-link>
</h1>
<h1
  v-else-if="htmlTag == 'h1'"
>
  <span>{{Name}}</span>
</h1>
<h2
  v-else-if="htmlTag == 'h2'"
>
  <span>{{Name}}</span>
</h2>
<h3
  v-else-if="htmlTag == 'h3'"
>
  <span>{{Name}}</span>
</h3>
<h4
  v-else-if="htmlTag == 'h4'"
>
  <span>{{Name}}</span>
</h4>
<h5
  v-else-if="htmlTag == 'h5'"
>
  <span>{{Name}}</span>
</h5>
<h6
  v-else-if="htmlTag == 'h6'"
>
  <span>{{Name}}</span>
</h6>
<dt
  v-else-if="htmlTag == 'dt'"
>
  <span>{{Name}}</span>
</dt>
<dt
  v-else-if="htmlTag == 'flogo'"
  class="serif"
>
  <nuxt-link to='/'>
    <span>{{Name}}</span>
  </nuxt-link>
</dt>
<span
  v-else
>
  {{Name}}
</span>
</template>

<script>
export default{
  htmlTag: 'SiteName',
  props:{
    htmlTag: String,
  },
  data(){
    return{
      Name:'cafe NORTH FOXES',
    }
  },
}
</script>
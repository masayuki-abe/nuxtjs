<template>
<h{{tagNumber}}><span>{{Name}}</span></h{{tagNumber}}>
</template>

<script>
export default{
  tagNumber: 'SiteName',
  props:['Htag'],
  data(){
    return{
      Name:'Simple Web Site.',
    }
  },
}
</script>
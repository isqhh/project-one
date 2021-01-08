<template>
  <div class="hot">
     <div class="head"></div>
  </div>
</template>

<script>
export default {
  name:'Hot',
  beforeRouteEnter(to, from, next){
     next(vm=>{
       vm.$http.get('top/list/?idx=1').then(data=>{
         console.log(data)
       })
     })
  }
}
</script>

<style lang="less" scoped>
   .head{
     width: 100%;
     height: 165px;
     background:url(../assets/hot_music_bg_2x.jpg) no-repeat;
     background-size: 100% 100%;
   }
</style>

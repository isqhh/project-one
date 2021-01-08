<template>
        <ul class="topnav">
            <li><router-link to="/">推荐歌单</router-link></li>
            <li><router-link to="/hot">热歌磅</router-link></li>
            <li><router-link to="/search">搜索</router-link></li>
        </ul>
</template>

<script>
export default {
  
}
</script>

<style lang="less" scoped>
    .topnav{
       display: flex;
       border-bottom: 1px solid #ccc;
       li{
           line-height: 40px;
           flex: 1;
           font-size: 15px;
           a{
               display: inline-block;
               text-decoration: none;
                color: #000;
               &.router-link-exact-active{
                   color:#e4393c;
                  border-bottom: 3px solid #e4393c;
               }
           }
       }
    }
</style>
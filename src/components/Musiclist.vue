<template>
  <ul>
    <router-link v-for="n in newMusicList" :key="n.id" to="/" tag="li">
      <div class="left">
        <div>{{ n.name }}</div>
        <p>
          <span class="sq" v-show="n.song.privilege.maxbr > 320000?true:false"></span
          ><span>{{ n.song.artists[0].name }}- {{ n.song.album.name }}</span>
        </p>
      </div>
      <div class="right">
        <span></span>
      </div>
    </router-link>
  </ul>
</template>

<script>
export default {
  name: "Musiclist",
  props: {
    newMusicList: Array,
    
    
  },
};
</script>

<style lang="less" scoped>
ul {
  li {
    width: 100%;
    height: 55px;
    padding: 8px;
    text-align: left;
    border-bottom: 1px solid rgb(243,243,244);
    display: flex;
    align-items: center;
    div.left {
      flex: 1;
      div {
        font-size: 17px;
      }
      p {
        color: #888;
        font-size: 12px;
        margin: 3px 0;
        span.sq {
          display: inline-block;
          width: 12px;
          height: 8px;
          margin-right: 4px;
          background: url(../assets/index_icon_2x.png) no-repeat;
          background-size: 166px 97px
        }
      }
    }
    div.right {
      span {
        display: inline-block;
        width: 22px;
        height: 22px;
        background: url(../assets/index_icon_2x.png) no-repeat;
        background-size: 166px 97px;
        background-position: -24px 0;
      }
    }
  }
}
</style>

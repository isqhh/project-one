<template>
  <div class="recommend">
    <Title>推荐歌单</Title>
    <ul>
      <router-link v-for="m in musicList" :key="m.id" tag="li" to="/">
        <div class="bg">
          <img :src="m.picUrl" />
          <span> {{ m.playCount | wan }} </span>
        </div>
        <div class="word">
          <span>{{ m.name }}</span>
        </div>
      </router-link>
    </ul>
     <Title >最新音乐</Title>
     <Musiclist :newMusicList='newMusicList'></Musiclist>
     <div class="ftwrap">
         <div class="logo"></div>
         <div class="openapp"></div>
         <p></p>
     </div>
  </div>
</template>

<script>
import Title from "../components/Title.vue";
import Musiclist from "../components/Musiclist.vue";
export default {
  name: "Recommend",
  components: {
    Title,
    Musiclist,
  },
  data() {
    return {
      musicList: [],
      newMusicList:[],
    };
  },
  filters: {
    wan(value) {
      return (value / 10000).toFixed(1) + "万";
    },
    // substr(value,leng){
    //   return value.substr(26,leng)+"..."
    // }
  },
  beforeRouteEnter(to, from, next){
    next((vm) => {
      vm.$http.get("/personalized?limit=6").then((data) => {
        vm.musicList = data.data.result;
      });
      vm.$http.get("/personalized/newsong?").then((data) => {
        vm.newMusicList = data.data.result;
        console.log(data)
      });
    });
  },
};
</script>


<style lang="less" scoped>
ul{
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  li {
    width: 33%;
    margin-bottom: 10px;
    div.word {
      height: 35px;
      padding: 0 5px;
      box-sizing: border-box;
      text-align: left;
      span {
        display: inline-block;
        width: 100%;
        height: 100%;
        font-size: 13px;
        overflow: hidden;
      }
    }
    div.bg {
      position: relative;
      span {
        position: absolute;
        top: 2px;
        right: 3px;
        color: #fff;
        text-shadow: 1px 1px 3px rgb(0, 0, 0, 0.5);
      }
    }
  }
}
  .ftwrap{
     width: 100%;
     height: 225px;
     background:url(../assets/recommand_bg_2x.png) no-repeat;
    //  background-size: 100% 100%;
  }
</style>

<template>
  <div id="page">
    <div style="left: 537px;">
      <searchBar></searchBar>
    </div>
    <div>
      <span>今日推荐</span>
      <!-- <v-card style="left: 146px;width: 390px;height: 549px;">
        <v-img :src="require('../assets/shiming.png')">
        </v-img>
      </v-card> -->
      {{recommendGift}}
    </div>
  </div>
</template>

<script>
import SearchBar from './SearchBar'
export default {
  name: 'Export',
  data () {
    return {
      recommendGift: [],
    }
  },
  components: {
    "searchBar": SearchBar
  },
  created () {
    this.$axios({
      method: "get",
      url: "http://fooxking.net:9000/search/QAQ",
    })
      .then((res) => {
        this.recommendGift = res.data;
      })
      .catch((error) => {
        console.log("失败了！");
      });
  }
}
</script>

<style scoped>
.Export {
  position: static;
  padding: 80px;
  margin: 120px auto 0 auto;
  height: 600px;
  width: 800px;
  background-color: rgba(255, 255, 255, 0.9);
}
h1 {
  padding: 0;
  font-size: 100px;
  text-align: center;
  color: rgba(50, 100, 150, 1);
}
</style>
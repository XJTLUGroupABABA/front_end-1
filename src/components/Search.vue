<template>
  <div class="background">
    <searchBar style="padding-top:40px;"></searchBar>

    <div class="word">
      搜索结果
    </div>
    <div style="display:flex">
      <v-card class="good_intro" v-for="(item, index) in relatedGift" :key="index">

        <v-img style="height:400px;width:400px;  align-items: center;" :src="item.gift_img"> </v-img>
        <div style="  font-size: 20px;color: black;font-family: Helvetica-regular;margin:10px;">
          {{item.gift_name}}
        </div>
      </v-card>
    </div>
  </div>
</template>

<script>
import SearchBar from './SearchBar'
export default {
  data () {
    return {
      loading: false,
      keyOfGift: this.$route.query.keyOfGift,
      showRelatedReasult: false,
      relatedGift: [],
    }
  },
  components: {
    "searchBar": SearchBar
  },
  methods: {
  },
  created () {
    this.$axios({
      method: "get",
      url: "http://fooxking.net:9000/search/" + this.keyOfGift,
    })
      .then((res) => {
        this.relatedGift = res.data;
        console.log(res);
      })
      .catch((error) => {
        console.log("失败了！");
      });
  }
}
</script>

<style scoped>
.background {
  background-color: pink;
  background-size: cover;
  height: 100%;
}
.word {
  font-size: 40px;
  color: aliceblue;
  font-family: Helvetica-regular;
  margin: 20px;
}
.good_intro {
  background-color: white;
  height: 500px;
  width: 500px;
  margin-left: 20px;
  margin-right: 20px;
}
</style>
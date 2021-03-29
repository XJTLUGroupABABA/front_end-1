<template>
  <div class="background">
    <searchBar style="padding-top:40px;"></searchBar>

    <div class="word">
      gifter found the following gifts for you~
    </div>
    <div style="display:flex;margin-left:65px;margin-right:65px">
      <v-card class="good_intro" v-for="(item, index) in relatedGift" :key="index">

        <v-img style="height:260px;width:260px;  align-items: center;" :src="item.gift_img"> </v-img>
        <div style="  font-size: 14px; color: black;font-family: Roboto;margin:10px;">
          {{item.gift_name}}
        </div>
        <span v-for="(tag, index) in item.gift_tag">
          <v-chip>{{tag}}</v-chip>
        </span>
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
        alert("没有找到任何礼物！");
      });
  }
}
</script>

<style scoped>
.background {
  background-color: pink;
  background-size: cover;
  height: 1200px;
}
.word {
  font-size: 30px;
  color: aliceblue;
  font-family: Helvetica-regular;
  margin-left: 92px;
  margin-bottom: 10px;
}
.good_intro {
  background-color: white;
  height: 400px;
  width: 275px;
  margin-left: 25px;
  margin-right: 25px;
  padding: 10px;
  border: 1px solid rgba(255, 255, 255, 100);
}
</style>
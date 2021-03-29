<template>
  <!--我不做人了（只是换到page_export去了）-->
  <div id="page">
    <div style="left: 537px;">
      <searchBar></searchBar>
    </div>
    <div>
      <span style="font-size:40px; color:rgba(255, 255, 255, 0.9);">今日推荐</span>
    </div>
    <v-app>
      <v-carousel
    cycle
    height="400"
    hide-delimiter-background
    show-arrows-on-hover
  >
    <v-carousel-item
      v-for="(slide, i) in slides"
      :key="i"
    >
      <v-sheet
        :color="colors[i]"
        height="100%"
      >
        <v-row
          class="fill-height"
          align="center"
          justify="center"
        >
          <div class="display-3">
            {{ slide }} Slide
          </div>
        </v-row>
      </v-sheet>
    </v-carousel-item>
  </v-carousel>
    </v-app>
     
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
    data () {
      return {
        colors: [
          'indigo',
          'warning',
          'pink darken-2',
          'red lighten-1',
          'deep-purple accent-4',
        ],
        slides: [
          'First',
          'Second',
          'Third',
          'Fourth',
          'Fifth',
        ],
      }
    },

  created () {
    this.$axios({
      method: "get",
      url: "http://fooxking.net:9000/search/泰迪熊",
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
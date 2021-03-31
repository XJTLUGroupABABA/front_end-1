<template>
  <v-card
      class="mx-auto"
      width="360px"
      tile
  >
    <v-list disabled>
      <v-subheader>Top 10 List</v-subheader>
      <v-list-item-group
          v-model="selectedItem"
          color="primary"
      >
        <v-list-item
            v-for="(item, i) in items"
            :key="i"
        >
          <v-list-item-icon>
            <!-- <v-icon v-text="item.icon"></v-icon> -->
            <v-img :src="item.icon" style="width: 12px; height: 20px; margin-right: 10px"></v-img>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title v-text="item.text"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-item-group>
    </v-list>
  </v-card>
</template>

<script>
export default {
name: "trends_list",
  data: () => ({
    selectedItem: 1,
    items: [
      { text: '泰迪熊', icon: require('../assets/fire.png')},
      { text: '出游C位连衣裙', icon: require('../assets/fire2.png')},
      { text: '春季T恤', icon: require('../assets/fire2.png') },
      { text: '通勤衬衣', icon: require('../assets/liWu.png') },
      { text: '甜酷气质西装杀', icon:require('../assets/liWu.png') },
      { text: '老爹鞋', icon: require('../assets/liWu.png') },
      { text: '全网超火的休闲裤', icon: require('../assets/liWu.png') },
      { text: '人气持妆散粉', icon: require('../assets/liWu.png') },
      { text: '开胃宝藏果脯', icon: require('../assets/liWu.png') },
      { text: '低卡魔芋蛋糕', icon: require('../assets/liWu.png') },
    ],
  }),
}
</script>

<style scoped>

</style>
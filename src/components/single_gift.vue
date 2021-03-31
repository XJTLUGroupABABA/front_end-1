<template>
  <div id="single_gift">
    <div class="outside">
      <ul class="bg">
        <div class="bg_left"></div>
        <div class="bg_right"></div>
        <img src="../assets/gift1.jpg" class="img1" />
        <img src="../assets/gift2.jpg" class="img2" />
      </ul>
      <h1>Bunnies By The Bay 14" Big Blossom Buddy Bunny Plush</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: "single_gift",
  methods: {},
};
</script>

<style scoped>
#single_gift {
  margin: 0;
  padding: 0;
  background: white;
  height: 900px;
  width: 100%;
}
.outside {
  background-color: #fcf5f5;
  border: 1px solid rgba(255, 255, 255, 100);
  box-shadow: 1px 1px 6px 2px rgba(0, 0, 0, 0.4);
  border-radius: 10px;
  position: absolute;
  width: 1220px;
  height: 900px;
  margin-top: 20px;
  margin-left: 20px;
  padding: 30px;
}

/* 左边的虚化图 */
.bg_left {
  background-image: url("../assets/gift1.jpg");
  width: 580px;
  height: 500px;
  position: absolute;
  list-style: none;
  filter: blur(2px);
}
/* 右边的虚化图 */
.bg_right {
  background-image: url("../assets/gift2.jpg");
  width: 500px;
  height: 500px;
  position: absolute;
  list-style: none;
  filter: blur(2px) !important;
  margin-left: 650px;
}
.img1 {
  width: 500px;
  position: relative;
  margin-left: 80px;
  transition: all 0.6s;
  border-right: 3px solid #fcf5f5;
}
.img2 {
  width: 500px;
  position: relative;
  transition: all 0.6s;
}
img:hover {
  transform: scale(1.1);
}

/* 文字设计 */
h1 {
  color: #D26F6C;
  font-size: 32px;
  text-align: left;
  font-family: SourceHanSansSC-regular;
  margin-top:50px;
}
</style>
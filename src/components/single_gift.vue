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
      <div class="detail">
        Let your little one discover endless cuddles with the Bun Bun Bunny
        Buddy Blanket from Bunnies by the Bay. Dressed in a velour and
        silky-satin trimmed blanket and soft fur, this stuffed animal can be
        personalized for a sentimental touch. The Bunnies by the Bay Bloom Bunny
        Bye Bye Buddy Blanket is a soft cuddly lovie friend for your little one
        Suitable for all ages Embroidery reads "Bloom" Can be personalized for a
        custom touch Velour with satin-like trim 100% polyester
      </div>
      <button class="click">Click to Buy</button> <br />
      <img class="likes" :src="like ? isLike : noLike" @click="changeLikes" />
      <img
        class="collection"
        :src="collection ? isCollection : noCollection"
        @click="changeCollection"
      />
      <div class="line"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "single_gift",
  data() {
    return {
      like: "",
      collection: "",
      noLike: require("../assets/loveBefore.png"),
      isLike: require("../assets/loveAfter.png"),
      noCollection: require("../assets/collectionBefore-2.png"),
      isCollection: require("../assets/collectionAfter.png"),
    };
  },
  methods: {
    changeLikes: function () {
      this.like = !this.like;
    },
    changeCollection: function () {
      this.collection = !this.collection;
    },
  },
};
</script>

<style scoped>
#single_gift {
  margin: 0;
  padding: 0;
  background: white;
  height: 1900px;
  width: 100%;
}
.outside {
  background-color: #fcf5f5;
  border: 1px solid rgba(255, 255, 255, 100);
  box-shadow: 1px 1px 6px 2px rgba(0, 0, 0, 0.4);
  border-radius: 10px;
  position: absolute;
  width: 1220px;
  min-height: 900px;
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
  color: #d26f6c;
  font-size: 32px;
  text-align: left;
  font-family: SourceHanSansSC-regular;
  margin-top: 50px;
}

/* 礼物详情介绍 */
.detail {
  width: 870px;
  min-height: 100px;
  margin-top: 30px;
  text-align: justify;
  line-height: 25px;
  font-family: Arial;
  font-size: middle;
  color: #424141;
}
.click {
  background-color: #d26f6c;
  border: none;
  color: white;
  padding: 15px 15px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  border-radius: 10px;
  font-family: SourceHanSansSC-regular;
  border: 1px solid rgba(210, 111, 108, 100);
  outline: none;
  margin-top: 40px;
}
.likes {
  width: 27px;
  margin-left: 790px;
  margin-top: 2px;
}
.collection {
  width: 27px;
  margin-left: 10px;
}
.line {
  left: 61px;
  width: 870px;
  height: 1px;
  border: 1px solid rgba(210, 111, 108, 0.7);
  margin-top:15px;
}
</style>
<template>
  <div>
    <div id="cover">
      <div class="tb">
        <div class="td">
          <input @keyup.enter.native="submit" type="text" v-model="keyOfGift" placeholder="Search for gift..." required>
        </div>
        <div class="td" id="s-cover">
          <router-link v-bind:to="{ path:'Search', query: { keyOfGift}}">
            <button @click="submit" :loading="loading" :disabled="loading">
              <div id="s-circle"></div>
              <span></span>
            </button>
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  data () {
    return {
      loading: false,
      keyOfGift: "",
      showRelatedReasult: false,
      relatedGift: [],
    }
  },
  watch: {
    infoSearch (val, oldVal) {
      if (val.length == 0) {
        this.showRelatedReasult = false
      } else {
        this.showRelatedReasult = true;
        this.relatedGift.forEach((item, index) => {
          if (item.indexOf(val) >= 0) {
            relatedGift.unshift(item)
          }
        })
        this.infoSearch = relatedGift;
      }
    }
  },
  methods: {
    submit () {
      this.$axios({
        method: "get",
        url: "http://fooxking.net:9000/search/" + this.keyOfGift,
      })
        .then((res) => {
          this.relatedGift = res.data;
          console.log("啊啊啊啊成功");
        })
        .catch((error) => {
          console.log("失败了！");
        });
    },
  },
};
</script>
<style scoped>
.autocomplete {
  display: inherit;
  margin-top: 280px;
  margin-left: 30%;
}
* {
  outline: none;
}

html,
body {
  height: 100%;
  min-height: 100%;
}

body {
  margin: 0;
  background-color: #ffd8d8;
}

.tb {
  display: table;
  width: 100%;
}

.td {
  display: table-cell;
  vertical-align: middle;
}

input,
button {
  color: #fff;
  font-family: Nunito;
  padding: 0;
  margin: 0;
  border: 0;
  background-color: transparent;
}

#cover {
  position: static;
  top: 140px;
  left: 0;
  right: 0;
  width: 604px;
  height: 130px;
  padding: 15px;
  margin: 0 auto 0 auto;
  background-color: #ff7575;
  border-radius: 20px;
  box-shadow: 0 10px 40px #ff7c7c, 0 0 0 20px #ffffffeb;
  transform: scale(0.6);
}

form {
  height: 96px;
}

input[type="text"] {
  width: 100%;
  height: 96px;
  font-size: 40px;
  margin-top: -30px;
  margin-left: 20px;
  line-height: 1;
}

input[type="text"]::placeholder {
  color: #e16868;
}

#s-cover {
  width: 1px;
  padding-left: 35px;
}

button {
  position: relative;
  display: block;
  width: 84px;
  height: 135px;
  cursor: pointer;
}

#s-circle {
  position: relative;
  top: -30px;
  left: 0;
  width: 60px;
  height: 60px;
  margin-top: 0;
  border-width: 15px;
  border: 15px solid #fff;
  background-color: transparent;
  border-radius: 50%;
  transition: 0.5s ease all;
}

button span {
  position: absolute;
  top: 68px;
  left: 43px;
  display: block;
  width: 45px;
  height: 15px;
  background-color: transparent;
  border-radius: 10px;
  transform: rotateZ(52deg);
  transition: 0.5s ease all;
}

button span:before,
button span:after {
  content: "";
  position: absolute;
  bottom: 0;
  right: 0;
  width: 45px;
  height: 15px;
  background-color: #fff;
  border-radius: 10px;
  transform: rotateZ(0);
  transition: 0.5s ease all;
}

#s-cover:hover #s-circle {
  top: -1px;
  width: 67px;
  height: 15px;
  border-width: 0;
  background-color: #fff;
  border-radius: 20px;
}

#s-cover:hover span {
  top: 50%;
  left: 56px;
  width: 25px;
  margin-top: -9px;
  transform: rotateZ(0);
}

#s-cover:hover button span:before {
  bottom: 11px;
  transform: rotateZ(52deg);
}

#s-cover:hover button span:after {
  bottom: -11px;
  transform: rotateZ(-52deg);
}
#s-cover:hover button span:before,
#s-cover:hover button span:after {
  right: -6px;
  width: 40px;
  background-color: #fff;
}

#ytd-url {
  display: block;
  position: fixed;
  right: 0;
  bottom: 0;
  padding: 10px 14px;
  margin: 20px;
  color: #fff;
  font-family: Nunito;
  font-size: 14px;
  text-decoration: none;
  background-color: #ff7575;
  border-radius: 4px;
  box-shadow: 0 10px 20px -5px rgba(255, 117, 117, 0.86);
  z-index: 125;
}

input::-webkit-input-placeholder {
  font-size: 36px;
  display: flex;
  align-items: center;
  color: #e16868;
}
.RelatedReasult {
  width: 300px;
  height: 50px;
}
.searchBar {
  display: flex;
  justify-content: center;
  width: 375px;
  height: 72px;
  margin-left: 30%;
}
</style>
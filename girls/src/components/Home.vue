<template>
  <div id="main-content" class="main-content" ref="bigbox">
    <link href="https://cdn.jsdelivr.net/npm/animate.css@3.5.1" rel="stylesheet" type="text/css">
    <input class="name-box" v-model="code" placeholder="输入你的名字~"/>
    <img src="@/assets/background.jpg" class="background">
    <img v-if = "typeof(decode_list[code]) === 'undefined'" src="@/assets/darkstar.png" class="get-pic-icon">
    <transition name="custom-classes-transition" enter-active-class="animated bounceIn" leave-active-class="animated bounceOut">
      <img v-if = "typeof(decode_list[code]) !== 'undefined'" src="@/assets/activestar.png" class="get-pic-icon">
    </transition>
    <div class="photo-box">
      <img :src="baseURL + decode_list[code]" class="cloud-pic" v-if = "typeof(decode_list[code]) !== 'undefined'">
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      code: '',
      baseURL: './static/cloud_pic/',
      decode_list: {
        '蔡': '30.png'
      }
    }
  },
  methods: {
    hideImg () {
      if (typeof (this.decode_list[this.code]) === 'undefined') {
        document.getElementsByClassName('cloud-pic')[0].style.display = 'inline'
      } else {
        document.getElementsByClassName('cloud-pic')[0].style.display = 'inline'
      }
    }
  },
  created () {
    // 获取当前可视区域的高度
    var height = document.documentElement.clientHeight
    // 在页面整体加载完毕时
    window.onload = function () {
    // 把获取到的高度赋值给根div
      document.getElementById('main-content').style.height = height + 'px'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main-content{
  position: absolute;
  top: 0px;
  bottom: 0px;
  height: 700px;
  width: 100%;
  overflow: scroll;
  z-index: 0;
}
.background{
  position: absolute;
  top: 0px;
  left: 0px;
  bottom: 0px;
  right: 0px;
  width: 100%;
  height: 100%;
}
.name-box{
  position: absolute;
  top: 15%;
  height: 5%;
  width: 44%;
  left: 27%;
  text-align: center;
  font-size: 15px;
  font-weight: 700;
  line-height: 15px;
  color: #FFFFFF;
  z-index: 2;
  background-color: transparent;
  border-radius: 20px 20px 20px 20px;
  border-style: dashed;
  border-width: 3px;
}
.get-pic-icon{
  position: absolute;
  top: 24%;
  left: 46%;
  height: 30px;
  width: 30px;
  border-radius: 25px;
}
.photo-box{
  position: absolute;
  bottom: 5%;
  height: 52%;
  width: 80%;
  left: 10%;
  z-index: 2;
  opacity: 0.95;
  border-radius: 10px 10px 10px 10px;
  box-shadow: 0 0 20px #AAA5A5;
}
.cloud-pic{
  position: relative;
  left: 3%;
  top: 3%;
  width: 94%;
  height: 94%;
  z-index: 3;
}
input::-webkit-input-placeholder{
  color: white;
}
input::-moz-placeholder{
  color: white;
}
input:-moz-placeholder{
  color: white;
}
input:-ms-input-placeholder{
  color: white;
}
</style>

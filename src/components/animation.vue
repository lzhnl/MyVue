<template>
  <div class="box">
    <h1>流量生成</h1>
    <el-button id="start" v-if="startButton" @click="start" icon="el-icon-caret-right">正常流量</el-button>
    <el-button id="end" v-if="endButton" @click="end" icon="el-icon-loading">结束流量</el-button>
   <div id="box1">
     <div class="picture"></div>
   </div>
    <el-button id="startBad" v-if="startBadButton" @click="startBad" icon="el-icon-caret-right">恶意流量</el-button>
    <el-button id="endBad" v-if="endBadButton" @click="endBad" icon="el-icon-loading">结束流量</el-button>
    <div id="box2">
    <div class="pictureBad"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "animation",
  data:function() {
  return {
    startButton:true,
    endButton:false,
    startBadButton:true,
    endBadButton:false,
  };
},
  methods:{
    start(){
      let x=document.getElementsByClassName('picture')
      let y=document.getElementById('box1')
      x[0].style.animationPlayState="running";
      y.style.animationPlayState='running';
     this.startButton=false;
     this.endButton=true;
    },
    startBad(){
      let x=document.getElementsByClassName('pictureBad')
      let y=document.getElementById('box2')
      x[0].style.animationPlayState="running";
      y.style.animationPlayState='running';
      this.startBadButton=false;
      this.endBadButton=true;
    },
    end(){
      let x=document.getElementsByClassName('picture')
      let y=document.getElementById('box1')
      x[0].style.animationPlayState="paused";
      y.style.animationPlayState='paused';
      this.startButton=true;
      this.endButton=false;
    },
    endBad(){
      let x=document.getElementsByClassName('pictureBad')
      let y=document.getElementById('box2')
      x[0].style.animationPlayState="paused";
      y.style.animationPlayState='paused';
      this.startBadButton=true;
      this.endBadButton=false;

    }
},


}
</script>

<style scoped>
.picture{
  overflow: hidden;
  width: 115px;
  height: 137px;
  background-image: url("../assets/流量.png");
  animation: run 1s steps(8) infinite ;
  animation-play-state: paused;
}
.pictureBad{
  flex: auto;
  width: 115px;
  height: 137px;
  background-image: url("../assets/恶意流量.png");
  animation:run 1s steps(8) infinite;
  animation-play-state: paused;
}
#box{
  width: 100%;
  height: 100%;
  overflow: hidden;
  margin-top: 150px;
}
#box1{
  width: 115px;
  height: 137px;
  position: absolute;
  animation: move 10s linear infinite;
  animation-play-state:paused ;
}
#box2{
  width: 115px;
  height: 137px;
  position: absolute;
  animation: move 10s linear infinite;
  animation-play-state:paused ;
}
button{
  margin: 20px;
  flex: 1;
}
@keyframes run {
  from{
    background-position: 0 0;
  }
  to{
    background-position: -920px ;
  }
}
@keyframes move {
  from {
  left: 0%;
  }
  /*创建关键帧*/
  25% {
    left: 25%;
  }

  50% {
    left: 50%;

  }
  75% {
    left: 75%;

  }
  to {
    left:90%;

  }
}
</style>
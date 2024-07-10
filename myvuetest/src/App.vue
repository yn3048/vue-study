
<template>

<div class="black-bg" v-if="modal == true">
  <div class="white-bg">
    <button @click="modal = false">X</button>
    <h4>상세페이지임</h4>
    <p>상세페이지 내용임</p>
  </div>
</div>

<div class="menu">
  <a v-for="name in menu" :key="name">{{name}}</a>
</div>
<div>

<div>
  <img class="roomImg" :src="rooms[0].image" alt="room1">
  <h4  @click="modal = true">{{rooms[0].title}}</h4>
  <p>{{rooms[0].price}}</p>
  <p>{{rooms[0].content}}</p>
  <button @click="report[0]++">허위매물신고</button> <span>신고수 : {{report[0]}}</span>
 </div>
 <div>
   <img class="roomImg" :src="rooms[1].image" alt="room2">
  <h4  @click="modal = true">{{rooms[1].title}}</h4>
  <p>{{rooms[1].price}}</p>
  <p>{{rooms[1].content}}</p>
  <button @click="report[1]++">허위매물신고</button> <span>신고수 : {{report[1]}}</span>
 </div>

<div>
   <img class="roomImg" :src="rooms[2].image" alt="room3">
  <h4  @click="modal = true"><p >{{rooms[2].title}}</p></h4>
  <p>{{rooms[2].price}}</p>
  <p>{{rooms[2].content}}</p>
  <button @click="report[2]++">허위매물신고</button> <span>신고수 : {{report[2]}}</span>
 </div>

 <div>
   <img class="roomImg" :src="rooms[3].image" alt="room3">
  <h4  @click="modal = true"><p >{{rooms[3].title}}</p></h4>
  <p>{{rooms[3].price}}</p>
  <p>{{rooms[3].content}}</p>
  <button @click="report[2]++">허위매물신고</button> <span>신고수 : {{report[3]}}</span>
 </div>


<div>
   <img class="roomImg" :src="rooms[4].image" alt="room3">
  <h4  @click="modal = true"><p >{{rooms[4].title}}</p></h4>
  <p>{{rooms[4].price}}</p>
  <p>{{rooms[4].content}}</p>
  <button @click="report[2]++">허위매물신고</button> <span>신고수 : {{report[4]}}</span>
 </div>


<div>
   <img class="roomImg" :src="rooms[5].image" alt="room3">
  <h4  @click="modal = true"><p >{{rooms[5].title}}</p></h4>
  <p>{{rooms[5].price}}</p>
  <p>{{rooms[5].content}}</p>
  <button @click="report[2]++">허위매물신고</button> <span>신고수 : {{report[5]}}</span>
 </div>



</div>
  
</template>

<script>

import deta from './assets/oneroom.js';

export default {
  name: 'App',
  data(){
    return{
      rooms : deta,
      modal : false,
      products : ['역삼동원룸', '서면원룸', '사상원룸'],
      menu : ['Home', 'Shop', 'About'],   
      price : ['110만원', '70만원', '40만원'],
      report : [0,0,0],
    }
  },
  methods : {
    increase(){
      this.report += 1;
    }
  },

  components: {

  }
}
</script>
 
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

div h4 {
  cursor: pointer;
}

.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
}

.white-bg {
  margin: 0 auto;
  position: relative;
  top: 50%;
  transform: translateY(-50%);
  width: 50%;
  height: 200px; 
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.white-bg button {
  position: absolute;
  right: 20px;
  width: 25px;
  height: 25px;
}

.menu {
  width: 100%;
  height: 80px;
  line-height: 80px;
  background-color: orange;
  color: #fff;
  border-radius: 5px;
}

.menu a {
  padding: 10px 20px;
}

.roomImg {
  width: 100%;
  margin-top: 40px;
}
</style>

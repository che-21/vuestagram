<template>
  <div class="header">
    <ul class="header-button-left">
      <li>Cancel</li>
    </ul>
    <ul class="header-button-right">
      <li>Next</li>
    </ul>
    <img src="./assets/logo.png" class="logo" />
  </div>

  <Container :insta="insta"/>
  <button @click="more">더보기</button>

  <div class="footer">
    <ul class="footer-button-plus">
      <input type="file" id="file" class="inputfile" />
      <label for="file" class="input-plus">+</label>
    </ul>
 </div>
</template>

<script>
import Container from './components/Container'
import insta from './assets/insta'
import axios from 'axios'
axios.post();
var num = 0;

export default {
  name: 'App',
  data(){
    return {
      insta : insta,
    }
  },
  components: {
    Container : Container,
  },
  methods : {
    more(){
      // 서버로 GET 요청해서 데이터 가져옴
      axios.get('https://codingapple1.github.io/vue/more'+num+'.json')
      
      /* 
      then()을 이용해서 GET/POST 요청 성공 이후 실행할 작업을 입력할 수 있음
      콜백함수 : 함수 안에 함수를 넣는 것 
      */
     .then( result =>{
       /* 
       function(){} 대신 ()=>{} 쓰는 것이 좋음
       일반함수는 this가 재정의 되나 arrow function을 사용하면 바깥에 있는 this를 그대로 사용함
       arrow function은 ()안의 파라미터가 1개면 소괄호 생략 가능
       */
      console.log(result.data);
      this.insta.push(result.data);
    })

    /* 실패시 실행할 코드는 .catch() */
    .catch( err =>{
      console.log(err);
      alert("오류!");
    })

    num++;
    
    }
  }
}
</script>

<style>
body {
  margin: 0;
}
ul {
  padding: 5px;
  list-style-type: none;
}
.logo {
  width: 22px;
  margin: auto;
  display: block;
  position: absolute;
  left: 0;
  right: 0;
  top: 13px;
}
.header {
  width: 100%;
  height: 40px;
  background-color: white;
  padding-bottom: 8px;
  position: sticky;
  top: 0;
}
.header-button-left {
  color: skyblue;
  float: left;
  width: 50px;
  padding-left: 20px;
  cursor: pointer;
  margin-top: 10px;
}
.header-button-right {
  color: skyblue;
  float: right;
  width: 50px;
  cursor: pointer;
  margin-top: 10px;
}
.footer {
  width: 100%;
  position: sticky;
  bottom: 0;
  padding-bottom: 10px;
  background-color: white;
}
.footer-button-plus {
  width: 80px;
  margin: auto;
  text-align: center;
  cursor: pointer;
  font-size: 24px;
  padding-top: 12px;
}
.sample-box {
  width: 100%;
  height: 600px;
  background-color: bisque;
}
.inputfile {
  display: none;
}
.input-plus {
  cursor: pointer;
}
#app {
  box-sizing: border-box;
  font-family: "consolas";
  margin-top: 60px;
  width: 100%;
  max-width: 460px;
  margin: auto;
  position: relative;
  border-right: 1px solid #eee;
  border-left: 1px solid #eee;
}
</style>

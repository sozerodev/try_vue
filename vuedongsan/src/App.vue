<template>

  <!-- <div class = "menu">
    <a href="">Home</a>
    <a href="">Products</a>
    <a href="">About</a>
  </div> -->

  <div class = "menu">
    <a v-for="작명 in 3" :key="작명">{{작명}} 테스트</a>
    <a v-for="item in menu" :key="item">{{item}}</a>

    <!-- 
      Vue의 HTML 반복문
      <태그 v-for="작명 in 몇회">

      vue 반복문 특)
      array/object 집어넣기 가능. 자료 안의 데이터 갯수만큼 반복된다. 

      <a v-for="(a, i) in 메뉴들" :key="i">{{a}} </a>
      여기서 왽꼬 변수 a는 array내의 데이터, 오른쪽 변수는 1씩 증가하는 index번호를 의미

     -->
  </div>
  

  <img alt="Vue logo" src="./assets/logo.png">
  <h1>logo</h1>
  <div :style = 'custom_style.blue'>
    <!-- html속성에 데이터 바인딩을 하고 싶다면
      :속성="데이터이름"  
      을 통해 데이터 바인딩도 가능하다.  -->
    <h4>xx 원룸</h4>
    <p >{{price1}}만원</p>
  </div>
  <div>
    <h4>{{ table.name }} 원룸</h4>
    <p>{{ table.price }} 만원</p>
  </div>
  
  <div v-for="item in products" v-bind:key="item">
    <h4>{{ item }} 원룸</h4>
    <p>?? 만원</p>
  </div>
  

</template>

<script>


export default {
  name: 'App',
  // vue의 데이터 보관함
  // vue의 실시간 자동 렌더링용
  // vue는 밑의 data를 변경하면 변경사항이 자동으로 html에 반영되며 재렌더링된다.
  // -> 따라서 웹앱같은 것들을 사용할 수 있게 됨
  data() {
    return {
      menu: ['Home', 'Shop', 'About'],
      price1: 60,
      table: {
        "name": "yy원룸하우스",
        "price": 70
      },
      custom_style: {
        "blue": "color: blue"
      },
      products: ['역삼동원룸', '천호동원룸', '마포동원룸']
      

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

.menu {
  background: darksalmon;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding-left: 10px;



}
</style>

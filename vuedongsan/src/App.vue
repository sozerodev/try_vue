<template>
  <!-- <div class = "menu">
    <a href="">Home</a>
    <a href="">Products</a>
    <a href="">About</a>
  </div> -->

  <ModalTest
    :product_info="product_info_list[selectedIdx]"
    :isModalOpen="isModalOpen"
    @closeModal="isModalOpen=false"
  />

  <!-- modal -->
  <!-- <div class="black-bg" v-if="isModalOpen">
    <div class="white-bg">
      <h3>{{ product_info_list[selectedIdx].title }}</h3>
      <h4>{{ product_info_list[selectedIdx].content }}</h4>
      <p>가격은 {{ product_info_list[selectedIdx].price }} 입니다!</p>
      <img :src="product_info_list[selectedIdx].image" alt="" />

      <br />
      <DiscountModal />

      <button @click="isModalOpen = false">닫기</button>
    </div>
  </div> -->

  <div class="menu">
    <a v-for="번호 in 3" :key="번호">{{ 번호 }} 테스트</a>
    <a v-for="item in menu" :key="item">{{ item }}</a>

    <!-- 
      Vue의 HTML 반복문
      <태그 v-for="작명 in 몇회">

      vue 반복문 특)
      array/object 집어넣기 가능. 자료 안의 데이터 갯수만큼 반복된다. 

      <a v-for="(a, i) in 메뉴들" :key="i">{{a}} </a>
      여기서 왽꼬 변수 a는 array내의 데이터, 오른쪽 변수는 1씩 증가하는 index번호를 의미

     -->
  </div>

  <img alt="Vue logo" src="./assets/logo.png" />
  <h1>logo</h1>
  <div :style="custom_style.blue">
    <!-- html속성에 데이터 바인딩을 하고 싶다면
      :속성="데이터이름"  
      을 통해 데이터 바인딩도 가능하다.  -->
    <h4>xx 원룸</h4>
    <p>{{ price1 }}만원</p>
  </div>
  <div>
    <h4>{{ table.name }} 원룸</h4>
    <p>{{ table.price }} 만원</p>
  </div>
  <button @click="warning_cnt++">허위매물 신고</button>
  <span>신고수: {{ warning_cnt }}</span> <br />

  <!-- 여러가지 이벤트 사용이 가능하다. mouseover를 체크하는 이벤트 핸들러 -->
  <button @mouseover="warning_cnt++">허위매물 신고</button>
  <span>마우스오버~: {{ warning_cnt }}</span>

  <hr />

  <div v-for="(item, idx) in products" v-bind:key="idx">
    <h4 @click="isModalOpen = true">{{ idx + 1 }}. {{ item }} 원룸</h4>
    <p>?? 만원</p>
    <button @click="warning_list[idx]++">허위매물 신고</button>
    <span>신고수: {{ warning_list[idx] }}</span> <br />
  </div>
  
  <hr />
  <!-- product_info_list -->

  <h1>카드컴포넌트</h1>
  <!-- <OneroomCard @openModal="(param) => {isModalOpen=true; selectedIdx = param}"  v-for="(item, idx) in product_info_list" :roomInfo="item" :key="idx"/> -->
  <OneroomCard @openModal="isModalOpen=true; selectedIdx = $event"  v-for="(item, idx) in product_info_list" :roomInfo="item" :key="idx"/>

  <hr> 
  <div v-for="(item, idx) in product_info_list" v-bind:key="idx">
    <h4
      @click="
        isModalOpen = true;
        selectedIdx = idx;
      "
    >
      {{ item.id + 1 }}. {{ item.title }}
    </h4>
    <!-- <h4 @click="openModal(idx)">{{ item.id + 1 }}. {{ item.title }}</h4> -->
    <img :src="item.image" alt="" />
    <div>{{ item.content }}</div>
    <p>{{ item.price }} 원</p>
    <button @click="warning_list[idx]++">허위매물 신고</button>
    <span>신고수: {{ warning_list[idx] }}</span> <br />
  </div>
</template>

<script>
import products from "@/assets/oneroom";
// import DiscountModal from "@/components/DiscountModal.vue";
import ModalTest from "@/components/ModalTest.vue";
import OneroomCard from "@/components/OneroomCard.vue";

export default {
  name: "App",
  // vue의 데이터 보관함
  // vue의 실시간 자동 렌더링용
  // vue는 밑의 data를 변경하면 변경사항이 자동으로 html에 반영되며 재렌더링된다.
  // -> 따라서 웹앱같은 것들을 사용할 수 있게 됨
  data() {
    return {
      modalData: "test",
      isModalOpen: false,
      selectedInfo: null,
      selectedIdx: null,
      warning_cnt: 0,
      warning_list: Array(products.length).fill(0),
      menu: ["Home", "Shop", "About"],
      price1: 60,
      table: {
        name: "yy원룸하우스",
        price: 70,
      },
      custom_style: {
        blue: "color: blue",
      },
      products: ["역삼동원룸", "천호동원룸", "마포동원룸"],
      product_info_list: products,
    };
  },
  components: {
    // DiscountModal,
    ModalTest,
    OneroomCard
  },
  methods: {
    openModal(idx) {
      console.log(idx);
      this.isModalOpen = true;
      this.selectedIdx = idx;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
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

body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>

<template>
  <div class="black-bg" v-if="isModalOpen">
    <div class="white-bg">
      <!-- <h3>{{ product_info_list[selectedIdx].title }}</h3>
      <h4>{{ product_info_list[selectedIdx].content }}</h4>
      <p>가격은 {{ product_info_list[selectedIdx].price }} 입니다!</p>
      <img :src="product_info_list[selectedIdx].image" alt="" />

      <br /> -->
      <DiscountModal />
      {{ product_info_list }}
      <!-- 부모컴포넌트로부터 받아온 값인 props는 read-only이다. 그렇기에 수정하면 에러가 남 -->
      <!-- <button @click="isModalOpen = false">닫기</button> -->

    </div>
  </div>
</template>
<script>
export default {
  name: "ModalTest",
  props: {
      product_info_list: Array,
      누른거: Boolean,
      isModalOpen: Boolean
    
  },
  components: {},
  data() {
    return {
      example: "",
    };
  },
  beforeCreate() {},
  created() {},
  beforeMount() {},
  mounted() {},
  beforeUpdate() {},
  updated() {},
  beforeUnmount() {},
  unmounted() {},
  methods: {},
};
</script>
<style></style>

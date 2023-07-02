<template>
  <div>
    <h4>{{ roomInfo.id + 1 }}. {{ roomInfo.title }}</h4>
    <img :src="roomInfo.image" alt="">
    <div>{{roomInfo.content}}</div>
    <div>{{ roomInfo.price }}원</div>
  </div>
</template>
<script>
export default {
  name: "OneroomCard",
  props: {
      roomInfo: Object,
  },
  components: {},
  data() {
    return {
      props: "",
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

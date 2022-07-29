<template>
  <!-- 모달창 -->
  <div class="black-bg" v-if="modalOpen === true">
    <div class="white-bg">
      <h3>{{ products[clickValue].title }}</h3>
      <p>{{ products[clickValue].content }}</p>
      <button v-on:click="modalOpen = false" class="modal-exit-btn">
        닫기
      </button>
    </div>
  </div>

  <div v-if="1 === 2">
    <p>안녕하세요</p>
  </div>

  <div v-else>
    <p>안녕못하세요</p>
  </div>

  <!-- 상품리스트 -->
  <div class="menu">
    <a v-for="(el, index) in menus" :key="index">{{ el }}</a>
  </div>
  <div v-for="(el, index) in products" :key="index">
    <img v-bind:src="el.image" class="room-img" />
    <h4
      v-on:click="
        modalOpen = true;
        clickValue = index;
      "
      class="product-name"
    >
      {{ el.title }}
    </h4>
    <p>{{ el.price }} ₩</p>
    <!-- <button v-on:click="el.report++">허위매물신고</button>
    <span>신고수: {{ el.report }}</span> -->
  </div>
</template>

<script>
import products from "./assets/data";
export default {
  name: "App",
  // 데이터 저장함 (변수선언)
  data() {
    return {
      products,
      menus: ["Home", "Products", "About"],
      modalOpen: false,
      clickValue: null,
    };
  },
  // 힘수저장함 (함수선언)
  methods: {},
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  display: flex;
  align-items: center;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background-color: white;
  padding: 20px;
  border-radius: 8px;
}

.modal-exit-btn {
  margin-top: 30px;
}

.modal-exit-btn:hover {
  cursor: pointer;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  /* border-radius: 5px; */
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}

.product-name {
  cursor: pointer;
}

.product-name:hover {
  text-decoration: underline;
}
</style>

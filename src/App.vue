<template>
  <!-- 모달창 -->
  <ModalWindow
    :products="products"
    :modalOpen="modalOpen"
    :clickValue="clickValue"
  />
  <!-- 헤더 -->
  <div class="menu">
    <a v-for="(el, index) in menus" :key="index">{{ el }}</a>
  </div>
  <!-- 배너 광고 -->
  <DiscountBanner />
  <!-- 상품리스트 -->
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
import DiscountBanner from "./components/DiscountBanner.vue";
import ModalWindow from "./components/ModalWindow.vue";

export default {
  name: "App",
  // 데이터 저장함 (변수선언)
  data() {
    return {
      products,
      menus: ["Home", "Products", "About"],
      modalOpen: false,
      clickValue: 0,
    };
  },
  // 힘수저장함 (함수선언)
  methods: {},
  components: {
    DiscountBanner: DiscountBanner,
    ModalWindow: ModalWindow,
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
  justify-content: center;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 400px;
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
  padding: 20px;
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

.discount {
  background: #eee;
  padding: 10px;
}
</style>

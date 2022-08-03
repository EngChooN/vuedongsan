<template>
  <!-- 모달창 -->
  <!-- 애니메이션 -->
  <!-- <div class="start" :class="{ end: modalOpen }">
    <ModalWindow
      :products="products"
      :modalOpen="modalOpen"
      :clickValue="clickValue"
      @openModal="modalOpen = $event"
    />
  </div> -->

  <!-- 뷰의 애니메이션 -->
  <transition name="fade">
    <ModalWindow
      :products="products"
      :modalOpen="modalOpen"
      :clickValue="clickValue"
      @openModal="modalOpen = $event"
    />
  </transition>

  <!-- 헤더 -->
  <div class="menu">
    <a v-for="(el, index) in menus" :key="index">{{ el }}</a>
  </div>
  <!-- 배너광고 -->
  <DiscountBanner />
  <!-- 상품리스트 -->
  <ProductCard
    v-for="(el, index) in products"
    :key="index"
    :el="el"
    :openModal="openModal"
    @openModal="
      modalOpen = true;
      clickValue = $event;
    "
  />
</template>

<script>
import products from "./assets/data";
import DiscountBanner from "./components/DiscountBanner.vue";
import ModalWindow from "./components/ModalWindow.vue";
import ProductCard from "./components/ProductCard.vue";

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
    ProductCard: ProductCard,
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
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 70%;
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

.start {
  opacity: 0;
  transition: all 0.3s;
}
.end {
  opacity: 1;
}

/* 입장 애니메이션 */
/* 시작 스타일 */
.fade-enter-from {
  opacity: 0;
}
/* transition */
.fade-enter-active {
  transition: all 0.3s;
}
/* 끝 스타일 */
.fade-enter-to {
  opacity: 1;
}

/* 퇴장 애니메이션 */
/* 시작 스타일 */
.fade-leave-from {
  opacity: 1;
}
/* transition */
.fade-leave-active {
  transition: all 0.3s;
}
/* 끝 스타일 */
.fade-leave-to {
  opacity: 0;
}
</style>

<template>
  <!-- 모달창 (애니메이션) -->
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
  <DiscountBanner v-if="showDiscountValid === true" />
  <!-- 정렬버튼 -->
  <div class="btn-wrapper">
    <button class="btn" @click="backSortClick">기본순</button>
    <button class="btn" @click="textSortClick">가나다순</button>
    <button class="btn" @click="priceSortLowClick">낮은가격순</button>
    <button class="btn last" @click="priceSortHighClick">높은가격순</button>
  </div>
  <!-- 반응형 정렬버튼 -->
  <div class="r-btn-wrapper">
    <div class="r-box1">
      <button class="r-btn margin" @click="backSortClick">기본순</button>
      <button class="r-btn" @click="textSortClick">가나다순</button>
    </div>
    <div class="r-box2">
      <button class="r-btn margin" @click="priceSortLowClick">
        낮은가격순
      </button>
      <button class="r-btn" @click="priceSortHighClick">높은가격순</button>
    </div>
  </div>
  <!-- 상품리스트 -->
  <ProductCard
    v-for="(el, index) in products"
    :key="index"
    :index="index"
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
import data from "./assets/data";

export default {
  name: "App",
  // 데이터 저장함 (변수선언)
  data() {
    return {
      // 스프레드를 이용하여 데이터의 사본을 만든다
      originProduct: [...data],

      products,
      menus: ["Home", "Products", "About"],
      modalOpen: false,
      clickValue: 0,
      showDiscountValid: false,
    };
  },
  // 힘수저장함 (함수선언)
  methods: {
    // 낮은 가격순 정렬 함수 (자바스크립트)
    priceSortLowClick() {
      this.products.sort(function (a, b) {
        return a.price - b.price;
      });
    },
    // 높은 가격순 정렬 함수 (자바스크립트)
    priceSortHighClick() {
      this.products.sort(function (a, b) {
        return b.price - a.price;
      });
    },
    // 정렬 되돌리기 (만들어 둔 원본 데이터를 이용 )
    backSortClick() {
      this.products = [...this.originProduct];
    },
    // 가나다순 정렬
    textSortClick() {
      this.products.sort(function (a, b) {
        return a.title.localeCompare(b.title);
      });
    },
  },
  components: {
    DiscountBanner: DiscountBanner,
    ModalWindow: ModalWindow,
    ProductCard: ProductCard,
  },
  mounted() {
    setTimeout(() => {
      this.showDiscountValid = true;
    }, 2000);
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
  width: 100%;
}

body {
  margin: 0;
  width: 100%;
  display: flex;
  justify-content: center;
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

.btn-wrapper {
  width: 100%;
  display: flex;
  justify-content: center;
}

.btn {
  margin-top: 40px;
  margin-right: 30px;
  background: darkslateblue;
  border: none;
  color: white;
  border-radius: 25px;
  padding: 10px;
  font-weight: 700;
  cursor: pointer;
  width: 100%;
  max-width: 100px;
}

.last {
  margin-right: 0px;
}

.r-btn-wrapper {
  width: 100%;
  display: none;
  flex-direction: column;
  justify-content: center;
}

.r-box01 {
  display: flex;
  justify-content: center;
  align-items: center;
}

.r-box02 {
  display: flex;
  justify-content: center;
  align-items: center;
}

.r-btn {
  margin-top: 40px;
  background: darkslateblue;
  border: none;
  color: white;
  border-radius: 25px;
  padding: 10px;
  font-weight: 700;
  cursor: pointer;
  width: 100%;
  max-width: 100px;
}

.margin {
  margin-right: 30px;
}

@media screen and (max-width: 575px) {
  .btn-wrapper {
    flex-direction: column;
    align-items: center;
    display: none;
  }

  .btn {
    margin-right: 0px;
  }

  .r-btn-wrapper {
    display: flex;
  }
}
</style>

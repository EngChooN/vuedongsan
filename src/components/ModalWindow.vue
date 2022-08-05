<template>
  <div class="black-bg" v-if="modalOpen === true">
    <div class="white-bg">
      <img :src="products[clickValue].image" class="room-img" />
      <h3>{{ products[clickValue].title }}</h3>
      <p>{{ products[clickValue].content }}</p>

      <!-- 같은 코드임! -->
      <!-- <input @input="month = $event.target.value" /> -->
      <input v-model="month" />

      <p>
        총 {{ month || 0 }} 개월 : {{ products[clickValue].price * month }} ₩
      </p>
      <DiscountBanner />
      <button v-on:click="modalClose" class="modal-exit-btn">닫기</button>
    </div>
  </div>
</template>

<script>
import DiscountBanner from "./DiscountBanner.vue";

export default {
  name: "ModalWindow",
  props: {
    products: Array,
    clickValue: Number,
    modalOpen: Boolean,
  },
  data() {
    return {
      month: 1,
    };
  },
  watch: {
    month(value) {
      // 숫자를 입력했는지
      if (isNaN(value)) {
        alert("숫자를 입력해 주세요!");
        this.month = 1;
        return;
      }

      // 입력값이 12이상인지
      if (value > 12) {
        alert("최대 12개월 입니다!");
        this.month = 1;
        return;
      }
    },
  },
  methods: {
    modalClose() {
      this.$emit("openModal", false);
    },
  },
  components: {
    DiscountBanner: DiscountBanner,
  },
  updated() {
    if (this.month == 2) {
      alert(
        "2를 입력 시, updated LifecycleHook이 동작하고 값은 1로 초기화 해줌!"
      );
      this.month = 1;
    }
  },
};
</script>

<style></style>

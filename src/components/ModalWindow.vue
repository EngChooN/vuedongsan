<template>
  <div class="black-bg" v-if="modalOpen === true">
    <div class="white-bg">
      <img :src="products[clickValue].image" class="room-img" />
      <h3>{{ products[clickValue].title }}</h3>
      <p>{{ products[clickValue].content }}</p>
      <input @input="month = $event.target.value" />
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
      month: 0,
    };
  },
  methods: {
    modalClose() {
      this.$emit("openModal", false);
    },
  },
  components: {
    DiscountBanner: DiscountBanner,
  },
};
</script>

<style></style>

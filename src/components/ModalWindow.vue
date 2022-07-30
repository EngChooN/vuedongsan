<template>
  <div class="black-bg" v-if="modalOpen === true">
    <div class="white-bg">
      <img :src="products[clickValue].image" class="room-img" />
      <h3>{{ products[clickValue].title }}</h3>
      <p>{{ products[clickValue].content }}</p>
      <p>{{ products[clickValue].price }} ₩</p>
      <DiscountBanner />
      <!-- <button v-on:click="modalOpen = false" class="modal-exit-btn">
        닫기
      </button> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalWindow",
  props: {
    products: Array,
    clickValue: Number,
    modalOpen: Boolean,
  },
  data() {
    return {};
  },
  methods: {},
};
</script>

<style></style>

<template>
  <!-- 상품리스트 -->
  <div>
    <img v-bind:src="el.image" class="room-img" />
    <h4 @click="$emit('openModal', index)" class="product-name">
      {{ el.title }}
    </h4>
    <p>{{ el.price }} ₩</p>
  </div>
</template>

<script>
export default {
  name: "ProductCard",
  props: {
    el: Array,
    openModal: Boolean,
    index: Number,
  },
};
</script>

<style></style>

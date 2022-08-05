<template>
  <!-- 배너 광고 -->
  <div class="discount">
    <h4>지금 결제하시면, {{ percent }}% 할인!!</h4>
  </div>
</template>

<script>
export default {
  name: "DiscountBanner",
  data() {
    return {
      percent: 10,
    };
  },
  mounted() {
    var timer = setInterval(() => {
      this.percent--;
      if (this.percent == 0) {
        // timer라는 변수에 담아서 clearInterval 함수로 종료
        clearInterval(timer);
      }
    }, 1000);
  },
};
</script>

<style></style>

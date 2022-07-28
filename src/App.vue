<template>
  <div class="menu">
    <a v-for="(el, index) in menus" :key="index">{{ el }}</a>
  </div>
  <div v-for="(el, index) in products" :key="index">
    <h4>{{ el.name }}</h4>
    <p>{{ el.price }} 만원</p>
    <button v-on:click="el.report++">허위매물신고</button>
    <span>신고수: {{ el.report }}</span>
  </div>
</template>

<script>
export default {
  name: "App",
  // 데이터 저장함 (변수선언)
  data() {
    return {
      products: [
        {
          name: "역삼동원룸",
          price: 60,
          report: 0,
        },
        {
          name: "천호동원룸",
          price: 70,
          report: 0,
        },
        {
          name: "마포구원룸",
          price: 100,
          report: 0,
        },
      ],
      menus: ["Home", "Products", "About"],
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

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}
</style>

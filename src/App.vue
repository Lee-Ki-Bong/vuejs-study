<template>
  <div class="black-bg" v-if="modal.is_open" @click="modalClose()">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
    </div>
  </div>

  <button v-on:click="modalOpen()">모달창</button>

  <img alt="Vue logo" src="logo.png" />
  <div v-for="(product, idx) in products" :key="idx" :id="idx">
    <img :src="product.image" class="p-img" alt="" />
    <h4>{{ product.name }}원룸</h4>
    <p>{{ product.price }} 만원</p>
    <button v-on:click="countUp(product)">허위매물신고</button>
    <span>신고수: {{ product.report_count }}</span>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      modal: {
        is_open: false,
      },
      products: [
        {
          name: '역삼동원룸',
          price: 50,
          report_count: 0,
          image: 'benjamin-rascoe-zNPlKIWCoZc-unsplash.jpg',
        },
        {
          name: '천호동원룸',
          price: 60,
          report_count: 0,
          image: 'dieter-blom-1sKrQtxJ_Ws-unsplash.jpg',
        },
        {
          name: '마포구원룸',
          price: 70,
          report_count: 0,
          image: 'dieter-blom-kokau7OYfe4-unsplash.jpg',
        },
      ],
    };
  },
  methods: {
    countUp(product) {
      product.report_count += 1;
    },
    modalOpen() {
      this.modal.is_open = true;
    },
    modalClose() {
      this.modal.is_open = false;
    },
  },
  components: {},
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
.p-img {
  width: 100%;
  margin-top: 40px;
}
</style>

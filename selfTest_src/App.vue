<template>
  <div class="black-bg" v-if="모달창current == true">
    <!-- 데이터에 따라 UI 어떻게 보일지 => 스위치 작성-->
    <div class="white-bg">
      <h4>post.js의 title을 넣고싶다!!</h4>
      <p>post.js의 content를 넣고싶다!!</p>
      <button @click="모달창current = false">닫기x</button>
    </div>
  </div>

  <div class="gnb">
    <!-- v-for와 :key를 같이 써야 함 -->
    <a :href="pageUrl[i]" v-for="(eachMenu, i) in gnbBtn" :key="i">{{
      gnbBtn[i]
    }}</a>
  </div>

  <div
    class="article"
    v-for="(상품, i) in 6"
    :key="i"
    @click="모달창current = true"
  >
    <img
      :src="데이터들[i].image"
      :alt="데이터들[i].title"
      :title="데이터들[i].title"
    />
    <h3>{{ 데이터들[i].title }}</h3>
    <p>{{ 데이터들[i].price }}</p>
  </div>

  <div
    class="article"
    v-for="(상품, i) in 3"
    :key="i"
    @click="모달창current = true"
  >
    <img src="https://via.placeholder.com/500x300" alt="sample" />
    <h4>{{ products[i] }}</h4>
    <p>{{ price[i] }} 만원</p>
    <button @click="increse">허위매물신고</button>
    <span> 신고수 : {{ for신고수 }} </span>
    <!-- 👆각각 카운트 증가하게 만들어 봐야함 -->
  </div>

  <!-- data binding -->
  <div class="article">
    <img src="https://via.placeholder.com/500x300" alt="sample" />

    <h4>{{ products[0] }}</h4>
    <p>{{ price[0] }} 만원</p>
    <button @click="신고수[0]++">허위매물신고</button>
    <span> 신고수 : {{ 신고수[0] }} </span>
  </div>
  <div class="article">
    <img src="https://via.placeholder.com/500x300" alt="sample" />

    <h4>{{ products[1] }}</h4>
    <p>{{ price[1] }} 만원</p>
    <button @click="신고수[1]++">허위매물신고</button>
    <span> 신고수 : {{ 신고수[1] }} </span>
  </div>
  <div class="article">
    <img src="https://via.placeholder.com/500x300" alt="sample" />

    <h4>{{ products[2] }}</h4>
    <p>{{ price[2] }} 만원</p>
    <button @click="신고수[2]++">허위매물신고</button>
    <span> 신고수 : {{ 신고수[2] }} </span>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import dummyDaya from "./data/post.js"; // 데이터들

export default {
  name: "App",
  data() {
    return {
      // react에서는 이 공간이 state(상태)
      데이터들: dummyDaya,
      모달창current: false, // 동적 UI 제작 1. 현재상태 기록 => 2번줄로
      for신고수: [],
      신고수: [0, 0, 0],
      pageUrl: ["http://naver.com", "http://google.com", "http://nate.com"],
      gnbBtn: ["고향사랑기부", "답례품", "고객센터", "mypage"],
      products: ["역삼동", "천호동", "마포구"],
      price: [50, 80, 70],
    };
  },
  // 함수자리 : data 아래, 함수안에서 데이터 쓸 땐, this.변수명
  methods: {
    increse() {
      this.for신고수++;
    },

    eachIncrease2() {
      // this.신고수[i]++;
    },
  },
  components: {},
};
</script>

<style scope>
#app {
  color: #2c3e50;
  text-align: center;
}
body {
  margin: 0;
  padding: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 80%;
  min-height: 300px;
  background-color: #fff;
  border-radius: 8px;
  padding: 20px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.gnb {
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 10px;
}
.gnb a {
  color: #fff;
  font-size: 2em;
  margin: 0 30px;
}

.article {
  width: 46%;
  margin: 2%;
  border: 1px solid #e1e1e1;
  padding: 30px;
  box-sizing: border-box;
  border-radius: 5px;
  display: inline-block;
}
.article img {
  width: 100%;
}
</style>

<template>
    <h1>영화정보</h1>

    <!-- <div>
      <h3 class="bg-yellow" :style="textRed">{{title}}</h3>
      <p>개봉: {{year}}</p>
      <p>장르: {{genre}}</p>
    </div> -->
    <div v-for="(item, i) in data" :key="i" class="item">
      <figure>
        <img :src="`${item.imgUrl}`" :alt="item.title">
      </figure>
      <div class="info">
        <h3 class="bg-yellow" :style="textRed">{{item.title}}</h3>
        <p>개봉: {{item.year}}</p>
        <p>장르: {{item.genre}}</p>
        <button @click="increaseLike(i)">좋아요</button> <span>{{ item.like }}</span>
        <p>
          <button @click="isModal=true">상세보기</button>
        </p>
      </div>
      <div v-if="isModal" class="modal">
        <div class="inner">
          <h3>Detail</h3>
          <p>영화 상세보기</p>
          <button @click="isModal=false">닫기</button>
        </div>
      </div>
    </div>

    <p v-for="(item, i) in foods" :key="i">{{item}}</p>
</template>

<script>
  export default {
    name: 'App',
    data() {
      return {
        isModal: false,
        data: [
          {
            title: "노량",
            year: 2023,
            genre: "액션, 드라마",
            imgUrl: './assets/노량.jpg',
            like: 0,
          },
          {
            title: "아쿠아맨과 로스트킹덤",
            year: 2023,
            genre: "액션, 판타지, 어드벤처",
            imgUrl: './assets/아쿠아맨.jpg',
            like: 0,
          },
          {
            title: "3일의 휴가",
            year: 2023,
            genre: "드라마",
            imgUrl: './assets/3일의휴가.jpg',
            like: 0,
          }, 
        ],
        textRed: "color: red"
      }
    },
    methods: {
      increaseLike(i) {
        this.data[i].like++;
      }
    }
  }
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
}

body {
  max-width: 768px;
  margin: 0 auto;
  padding: 20px;
}

h1,
h2,
h3 {
  margin-bottom: 1rem;
}

p {
  margin-bottom: 0.5rem;
}

button {
  margin-right: 10px;
  margin-top: 1rem;
}

.item {
  width: 100%;
  border: 1px solid #ccc;
  display: flex;
  margin-bottom: 20px;
  padding: 1rem;
}

.item figure {
  width: 30%;
  margin-right: 1rem;
}

.item img {
  width: 100%;
}

.item .info {
  width: 100%;
}

.modal {
  background: rgba(0, 0, 0, 0.4);
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal .inner {
  background: #fff;
  width: 80%;
  padding: 20px;
  border-radius: 10px;
}
</style>

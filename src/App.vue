<template>
    <Navbar />
    <h1>영화정보</h1>

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
          <button @click="isModal=true; selectedMovie=i">상세보기</button>
        </p>
      </div>
    </div>
    <Modal />

    <p v-for="(item, i) in foods" :key="i">{{item}}</p>
</template>

<script>
  import Navbar from './components/Navbar.vue';
  import Modal from './components/Modal.vue';
  import data from './assets/movies';
  console.log(data);
  export default {
    name: 'App',
    data() {
      return {
        isModal: false,
        data: data,
        selectedMovie: 0,
      }
    },
    methods: {
      increaseLike(i) {
        this.data[i].like++;
      }
    },
    components: {
      Navbar: Navbar,
      Modal: Modal,
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

<template>
    <h1>영화정보</h1>

    <!-- <div>
      <h3 class="bg-yellow" :style="textRed">{{title}}</h3>
      <p>개봉: {{year}}</p>
      <p>장르: {{genre}}</p>
    </div> -->
    <div v-for="(item, i) in data" :key="i">
      <h3 class="bg-yellow" :style="textRed">{{item.title}}</h3>
      <p>개봉: {{item.year}}</p>
      <p>장르: {{item.genre}}</p>
      <button @click="increaseLike(i)">좋아요</button> <span>{{ item.like }}</span>
    </div>

    <p v-for="(item, i) in foods" :key="i">{{item}}</p>
</template>

<script>
  export default {
    name: 'App',
    data() {
      return {
        foods: ["김밥", "순대", "만두"],
        data: [
          {
            title: "노량",
            year: 2023,
            genre: "액션, 드라마",
            like: 0,
          },
          {
            title: "아쿠아맨과 로스트킹덤",
            year: 2023,
            genre: "액션, 판타지, 어드벤처",
            like: 0,
          }  
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
  .bg-yellow {
    background: gold;
  }
</style>

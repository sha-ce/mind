<template>
  <div class="wrap">
    <h1>こころのグラフ</h1>
    <h3>- こころの仕組みをグラフにする -</h3>
    <p>選択肢：「はい:2」「いいえ:0」「どちらでもない:1」</p><br>
    <p>「どちらもでもない」が少ないほどはっきりしたグラフができます．以下の問題に答えてください．</p><br>
    <br><br>
    <form method="post" novalidate="true" @submit.prevent>
      <button @click="submit">診断開始</button>
    </form>
    <br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  methods: {
    submit() {
      this.$router.push('./question')
    }
  }
}
</script>

<style scoped>
.wrap {
  padding: 30px;
}
h1 {
  padding: 30px;
}
button {
  margin: 10px;
  padding: 10px 20px;
  font-size: 2rem;
  border: none;
  box-shadow: 1px 0 4px 3px lightgray;
  background: white;
  cursor: pointer;
}
button:hover {
  background: gray;
  color: white;
  transition: ease;
}
</style>

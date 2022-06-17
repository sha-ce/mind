<template>
  <div>
    <Header/>
    <Menu/>
    <br><br>
    <div class="question">
    <div class="one">
      <form method="post" novalidate="true" @submit.prevent>
        <div class="sentence">{{ index+1+': '+sentences[index] }}</div>
        <div calss="labels">
          <label><input type="radio" v-model="pick" value="2" @click="submit">はい</label>
          <label><input type="radio" v-model="pick" value="1" @click="submit">どちらでもない</label>
          <label><input type="radio" v-model="pick" value="0" @click="submit">いいえ</label>
        </div>
      </form>
    </div>
  </div>
  <Footer/>
  <div id="stage"></div>
  </div>
</template>

<script src="https://cdnjs.cloudflare.com/ajax/libs/canvasjs/1.7.0/canvasjs.min.js"></script>
<script>
export default {
  data() {
    return {
      index: 0,
      pick: -1,
      line: ['CP', 'NP', 'A', 'FC', 'AC'],
      column: [],
      sentences: [
        '間違ったことに対して，間違いだとはっきり言う．',
        '思いやりがある．',
        '何が問題の中心かを考える．',
        'してみたいことがいっぱいある．',
        '人の気持ちに合わせてしまう．',
        '気分転換が上手だ．',
        '人をほめるのが上手だ．',
        '時間を守らないことは嫌いだ．',
        '物事を事実に基づいて考える．',
        '人前に出るより，後ろに引っ込んでしまう．',
        '人の話をよく聞いてあげることが多い．',
        'よく後悔する．',
        '規則やルールを守る．',
        'よく笑う．',
        'なぜそうなるのか，理由を考える．',
        '相手の顔色を見てどうするかを決める．',
        'いろいろなものに興味がある．',
        '悪い結果の原因を厳しく追及する．',
        '筋道を立てて考える．',
        '人の気持ちを考える．',
        '新聞やテレビのニュースに関心がある．',
        'ちょっとした贈り物でもしたい．',
        '不愉快なことがあっても口に出さない．',
        '「～すべきである」「～ねばならない」とよく言う．',
        '物事を前向きに考える．',
        '人の失敗を許す．',
        '人に良く思われようと振る舞う．',
        '決めたことは最後まで守らないと気が済まない．',
        'ユーモアがある．',
        '結末を予測して，準備をする．',
        'お金を借りたら，期限までに返さないと気になる．',
        '人の意見や行動に合わせることができる．',
        '新しいことが好きだ．',
        '物事を落ち着いて判断する．',
        '人の世話をするのが好きだ．',
        'すぐ遠慮してしまう．',
        'わからないときはわかるまで考える．',
        '約束を破らない．',
        '自分から挨拶する．',
        '楽しいことを空想するのが好きだ．',
        '日記をつけたり生活の予定を記録する．',
        '子供や年下の人をかわいがる．',
        '趣味がたくさんある．',
        '正しくないことは放っておけない．',
        '周りの人の意見に振り回される．',
        '「すごい」「わあー」などの言葉をよく使う．',
        '無責任な人を見ると許せない．',
        '悪くもないのにすぐ謝る．',
        '他の人ならどうするだろうかと考える．',
        '困っている人を見ると何とかしてあげたくなる．', 
      ],
      numAll: {
        numCP: [1,8,13,18,24,28,31,38,44,47],
        numNP: [2,7,11,20,22,26,35,39,42,50],
        numA : [3,9,15,19,21,30,34,37,41,49],
        numFC: [4,6,14,17,25,29,33,40,43,46],
        numAC: [5,10,12,16,23,27,32,36,45,48],
      },
      sumAll: [0,0,0,0,0],
    }
  },
  methods: {
    submit() {
      this.column[this.index] = this.pick
      if(this.index >= 49) {
        // this.$router.push('./result')
        this.column[this.index] = this.pick
        this.calc()
        this.graph()
      }
      this.index++
      this.$router.push('./question')
    },
    calc() {
      for(let n = 0; n < 10; n++) {
        this.sumAll[0] += parseInt(this.column[this.numAll.numCP[n]])
      } for(let n = 0; n < 9; n++) {
        this.sumAll[1] += parseInt(this.column[this.numAll.numNP[n]])
      } for(let n = 0; n < 10; n++) {
        this.sumAll[2] += parseInt(this.column[this.numAll.numA[n]])
      } for(let n = 0; n < 10; n++) {
        this.sumAll[3] += parseInt(this.column[this.numAll.numFC[n]])
      } for(let n = 0; n < 10; n++) {
        this.sumAll[4] += parseInt(this.column[this.numAll.numAC[n]])
      }
      this.sumAll[1] += parseInt(this.column[this.index])
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
.one {
  width: min(90vw, 1000px);
  text-align: center;
  margin: 100px auto;
  padding: 50px 0;
  border-radius: 5px;
  box-shadow: 0 0 8px #00000029;
}

.sentence {
  padding: 30px;
}
.labels {
  display: inline-block;
  padding: 20px;
  margin: 0 10%;
}
input[type=radio] {
  display: none;
}
label {
  width: 20px;
  height: 10px;
  margin: 30px 10px;
  padding: 10px;
  box-shadow: 1px 0 4px 3px lightgray;
  border-radius: 2px;
  cursor: pointer;
}
label:active {
  background: gray;
  color: white;
}
</style>

<template>
  <div class="hello">
    <header>
      <h1>{{ appName }}</h1>
    </header>
    <h3>上の段</h3>
    <div class="input_text">
      <input class="form-control" id="title_top" v-model="titleTop">
    </div>
    <h3>下の段</h3>
    <div class="input_text">
      <input class="form-control" id="title_bottom" v-model="titleBottom">
    </div>
    <div class="row">
      <div class="col-sm-6">
        <p>左側</p>
        <input type="text" class="form-control" id="left_cap" v-model="leftCap">
      </div>
      <div class="col-sm-6">
        <p>左側</p>
        <input type="text" class="form-control" id="right_cap" v-model="rightCap">
      </div>
    </div>
    <div class="submit">
      <button type="button" class="btn btn-success" id="enter" @click="generate">嵐を呼ぶ!</button>
      <button type="button" class="btn btn-success" id="tweet">嵐をシェアする!</button>
      <a href="https://twitter.com/intent/tweet?&hashtags=嵐を呼ぶジェネレータ&url=https://afterschoolstudy.github.io/generator_of_call_a_storm/dist/" class="twitter-hashtag-button" data-show-count="false">Tweet #嵐を呼ぶジェネレータ</a>
    </div>
    <div class="output">
      <canvas id="output_field" width="2880" height="1620"></canvas>
      <img id="output_image" />
    </div>
    <footer>
      <p>powered by ITCreateClub</p>
    </footer>
  </div>
</template>
<script>
export default {
  name: 'Generator',
  data () {
    return {
      appName: '嵐を呼ぶサブタイトルジェネレータ',
      titleTop: 'タイトル',
      titleBottom: 'ジェネレーターだゾ',
      leftCap: '脚本 : フロント 太郎',
      rightCap: '監督 : エンド 次郎'
    }
  },
  methods: {
    generate () {
      this.drawBg()
      let ctx = document.getElementById('output_field').getContext('2d')
      ctx.clearRect(0, 0, 2880, 1620)
      this.drawBg()

      // 嵐部分
      ctx.font = '250px sans-serif'
      ctx.textAlign = 'left'
      let topText = this.titleTop
      let bottomText = this.titleBottom
      ctx.fillStyle = '#5853A0'
      ctx.fillText(topText, 140, 590)
      ctx.textAlign = 'right'
      ctx.fillText(bottomText, 2740, 930)

      // 左キャプション
      let leftCap = this.leftCap
      ctx.textAlign = 'left'
      ctx.lineWidth = 5
      ctx.fillStyle = '#FFF'
      ctx.font = '90px cursive'
      ctx.fillText(leftCap, 400, 1350)
      ctx.strokeStyle = 'gray'
      ctx.strokeText(leftCap, 400, 1350)

      // 右キャプション
      let rightCap = this.rightCap
      ctx.textAlign = 'right'
      ctx.lineWidth = 5
      ctx.fillStyle = '#FFF'
      ctx.font = '90px cursive'
      ctx.fillText(rightCap, 2480, 1350)
      ctx.strokeStyle = 'gray'
      ctx.strokeText(rightCap, 2480, 1350)

      // 生成
      ctx = document.getElementById('output_field')
      let png = ctx.toDataURL()
      document.getElementById('output_image').src = png
      $('#output').css('border', '0')
      $('#output_field').hide()
      $('#output_image').show()
    },
    drawBg () {
      let ctxBase = document.getElementById('output_field').getContext('2d')
      ctxBase.beginPath()
      let ctxBaseColor = ctxBase.createLinearGradient(0, 410, 0, 1620)
      ctxBaseColor.addColorStop(0.0, '#FD81A6')
      ctxBaseColor.addColorStop(1.0, '#FFFF83')
      ctxBase.fillStyle = ctxBaseColor
      ctxBase.fillRect(0, 0, 2880, 1620)
    }
  }
}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
}
h1, p{
  margin:0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
header{
  max-width: 960px;
  margin: 0 auto;
  text-align: left;
  border-bottom: 1px solid gray;
}
header h1{
  font-size: 2rem;
}
.input_text{
  max-width: 960px;
  margin: 0 auto;
}
.input_text input{
  margin: 0 0 20px 0;
}
h3{
  margin: 0 auto;
  text-align: left;
  max-width: 960px;
}
@media screen and (max-width: 960px){
  h3{
    font-size:1.4rem;
  }
}
.row{
  max-width: 960px;
  margin: 0 auto;
}
.row div{
  padding: 0;
}
.row p{
  text-align: left;
  margin-bottom: 0;
}
.submit{
  max-width: 960px;
  margin: 0 auto;
  margin-bottom: 15px;
  text-align:right;
}
.submit #enter, .submit #tweet{
  margin-top: 20px;
  width: 100%;
}
#tweet{
  background-color: royalblue;
  border-color: mediumblue;
}
#tweet:hover{
  background-color: #3453b3;
}
.output{
  width: 960px;
  height: 540px;
  margin: 0 auto;
  border: 1px solid gray;
}
.output #output_field{
  width: 100%;
  height: 100%;
  font-size: 50px;
}
.output #output_image{
  max-width: 960px;
  display: none;
}
@media screen and (max-width: 960px){
  .output{
    width: 100vw;
    height: calc( 100vw * 0.536);
  }
  .output #output_image{
    width: 100%;
    height: 100%;
  }
}
footer{
  height: 30px;
  margin-top: 25px;
  border-top: 1px solid gray;
}
</style>

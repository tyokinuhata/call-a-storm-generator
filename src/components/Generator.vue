<template>
  <div>
    <header class="mt-2">
      <h1>{{ appName }}</h1>
    </header>
    <div class="container">
      <div class="mb-2">
        <div class="row mb-2">
          <div class="col-md-1">上の段</div>
          <input class="form-control d-inline col-md-11" v-model="titleTop" autofocus>
        </div>
        <div class="row mb-2">
          <div class="col-md-1">下の段</div>
          <input class="form-control d-inline col-md-11" v-model="titleBottom">
        </div>

        <div class="row mb-2">
          <div class="col-md-1">左側</div>
          <input class="form-control d-inline col-md-11" v-model="leftCap">
        </div>
        <div class="row mb-2">
          <div class="col-md-1">右側</div>
          <input class="form-control d-inline col-md-11" v-model="rightCap">
        </div>
      </div>

      <div class="row mb-2">
        <button type="button" class="col-md-6 btn btn-success" @click="generate">嵐を呼ぶ！</button>
        <a href ="https://twitter.com/intent/tweet?&hashtags=嵐を呼ぶジェネレータ&url=https://afterschoolstudy.github.io/generator_of_call_a_storm/dist/" class="col-md-6 btn btn-primary">嵐をシェアする！</a>
      </div>

      <div class="output">
        <canvas id="output_field" width="2880" height="1620"></canvas>
        <img id="output_image" />
      </div>
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
      let ctx = document.getElementById('output_field').getContext('2d')
      ctx.clearRect(0, 0, 2880, 1620)
      this.drawBg()

      // 嵐部分
      ctx.font = '250px sans-serif'
      ctx.textAlign = 'left'
      const topText = this.titleTop
      const bottomText = this.titleBottom
      ctx.fillStyle = '#5853A0'
      ctx.fillText(topText, 140, 590)
      ctx.textAlign = 'right'
      ctx.fillText(bottomText, 2740, 930)

      // 左キャプション
      const leftCap = this.leftCap
      ctx.textAlign = 'left'
      ctx.lineWidth = 5
      ctx.fillStyle = '#FFF'
      ctx.font = '90px cursive'
      ctx.fillText(leftCap, 400, 1350)
      ctx.strokeStyle = 'gray'
      ctx.strokeText(leftCap, 400, 1350)

      // 右キャプション
      const rightCap = this.rightCap
      ctx.textAlign = 'right'
      ctx.lineWidth = 5
      ctx.fillStyle = '#FFF'
      ctx.font = '90px cursive'
      ctx.fillText(rightCap, 2480, 1350)
      ctx.strokeStyle = 'gray'
      ctx.strokeText(rightCap, 2480, 1350)

      // 生成
      ctx = document.getElementById('output_field')
      document.getElementById('output_image').src = ctx.toDataURL()
      $('#output').css('border', '0')
      $('#output_field').hide()
      $('#output_image').show()
    },
    drawBg () {
      const ctxBase = document.getElementById('output_field').getContext('2d')
      ctxBase.beginPath()
      const ctxBaseColor = ctxBase.createLinearGradient(0, 410, 0, 1620)
      ctxBaseColor.addColorStop(0.0, '#FD81A6')
      ctxBaseColor.addColorStop(1.0, '#FFFF83')
      ctxBase.fillStyle = ctxBaseColor
      ctxBase.fillRect(0, 0, 2880, 1620)
    }
  }
}
</script>

<style lang="scss" scoped>
  h1, h2 {
    font-weight: normal;
  }
  h1, p {
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
  header {
    max-width: 960px;
    margin: 0 auto 10px auto;
    text-align: left;
    border-bottom: 1px solid gray;
    padding-top: 20px;
    h1{
      font-size: 2rem;
    }
  }
  .input_text {
    max-width: 960px;
    margin: 0 auto;
    input{
      margin: 0 0 20px 0;
    }
  }
  h3{
    margin: 0 auto;
    text-align: left;
    max-width: 960px;
  }
  @media screen and (max-width: 960px) {
    h3{
      font-size:1.4rem;
    }
  }
  .row {
    max-width: 960px;
    margin: 0 auto 20px auto;
    div{
      padding: 0;
    }
    p{
      text-align: left;
      margin-bottom: 0;
    }
  }
  .submit {
    max-width: 960px;
    margin: 0 auto 15px auto;
    text-align:right;
    #enter, #tweet {
      margin-bottom: 20px;
      width: 100%;
    }
  }
  #tweet {
    background-color: royalblue;
    border-color: mediumblue;
    &:hover{
      background-color: #3453b3;
    }
  }
  .output {
    max-width: 960px;
    height: 540px;
    margin: 0 auto 25px auto;
    border: 1px solid gray;
    @media screen and (max-width: 960px) {
      width: 100%;
      height: calc( 100vw * 0.536);
    }
    #output_field {
      width: 100%;
      height: 100%;
      font-size: 50px;
    }
    #output_image {
      max-width: 960px;
      display: none;
      @media screen and (max-width: 960px) {
        width: 100%;
        height: 100%;
      }
    }
  }
  footer {
    height: 30px;
    border-top: 1px solid gray;
  }
  .c-container {
    padding: 0;
    @media screen and (max-width: 960px) {
      padding: 0 20px;
    }
  }
</style>

<template>
  <div>
    <header class="mt-2 mr-1 ml-1">
      <h1 class="h1">{{ appName }}</h1>
    </header>
    <div class="container">
      <div class="mb-2">
        <div class="row mb-2 mr-1 ml-1">
          <div class="col-md-1">上の段</div>
          <input class="form-control d-inline col-md-5" v-model="titleTop" autofocus>

          <div class="col-md-1">下の段</div>
          <input class="form-control d-inline col-md-5" v-model="titleBottom">
        </div>

        <div class="row mb-2 mr-1 ml-1">
          <div class="col-md-1">左側</div>
          <input class="form-control d-inline col-md-5" v-model="leftCap">

          <div class="col-md-1">右側</div>
          <input class="form-control d-inline col-md-5" v-model="rightCap">
        </div>

        <div class="row mb-2 ml-1">
          <div class="col-md-1">配色</div>
          <select class="form-control col-md-2" v-model="colorType">
            <option>桃 ~ 黃</option>
            <option>緑 ~ 白 ~ 青</option>
          </select>
        </div>
      </div>

      <div class="row mb-2 mr-1 mr-1 ml-1">
        <button type="button" class="col-md-6 btn btn-success" @click="generate">嵐を呼ぶ！</button>
        <a href ="https://twitter.com/intent/tweet?&hashtags=嵐を呼ぶジェネレーター&url=https://afterschoolstudy.github.io/generator_of_call_a_storm" class="col-md-6 btn btn-primary">嵐をシェアする！</a>
      </div>

      <div class="mb-4">
        <canvas id="output_field" width="2880" height="1620" v-show="!isGenerated"></canvas>
        <img class="output_image" :src="src" v-show="isGenerated" />
      </div>
    </div>
    <footer class="border-top pt-3">
      <p>
        Powered by <a href="https://itc.moe/" target="_blank">IT Create Club</a>
        &#x1f300;
        Fork me on <a href="https://github.com/AfterSchoolStudy/generator_of_call_a_storm" target="_blank">GitHub</a>
      </p>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'Generator',
  data () {
    return {
      appName: '嵐を呼ぶサブタイトルジェネレーター',
      titleTop: '嵐を呼ぶサブタイトル',
      titleBottom: 'ジェネレーターだゾ',
      leftCap: '脚本 : ごめんね',
      rightCap: '監督 : おらもう',
      colorType: '桃 ~ 黃',
      src: '',
      isGenerated: false
    }
  },
  mounted () {
    this.generate()
  },
  methods: {
    generate () {
      // 描画
      let ctx = document.getElementById('output_field').getContext('2d')
      this.drawBg(ctx, this.colorType)
      this.drawTitle(ctx, this.colorType)
      this.drawCaption(ctx, this.leftCap, 'left', { 'x': 400, 'y': 1350 })
      this.drawCaption(ctx, this.rightCap, 'right', { 'x': 2480, 'y': 1350 })

      // 生成
      ctx = document.getElementById('output_field')
      this.isGenerated = true
      this.src = ctx.toDataURL()
    },
    drawTitle (ctx, colorType) {
      ctx.font = '250px sans-serif'
      ctx.textAlign = 'left'
      ctx.fillStyle = colorType === '桃 ~ 黃' ? '#5853A0' : '#633EBF'
      ctx.fillText(this.titleTop, 140, 590)
      ctx.textAlign = 'right'
      ctx.fillText(this.titleBottom, 2740, 930)
    },
    drawCaption (ctx, text, align, coordinate) {
      ctx.textAlign = align
      ctx.lineWidth = 5
      ctx.fillStyle = '#FFF'
      ctx.font = '90px cursive'
      ctx.fillText(text, coordinate['x'], coordinate['y'])
      ctx.strokeStyle = 'gray'
      ctx.strokeText(text, coordinate['x'], coordinate['y'])
    },
    drawBg (ctx, colorType) {
      ctx.beginPath()
      const ctxBaseColor = ctx.createLinearGradient(0, 410, 0, 1620)

      if (colorType === '桃 ~ 黃') {
        ctxBaseColor.addColorStop(0.0, '#FD81A6')
        ctxBaseColor.addColorStop(1.0, '#FFFF83')
      } else {
        ctxBaseColor.addColorStop(0.0, '#AEEC97')
        ctxBaseColor.addColorStop(0.3, '#FFF')
        ctxBaseColor.addColorStop(1.0, '#73B2F9')
      }
      ctx.fillStyle = ctxBaseColor
      ctx.fillRect(0, 0, 2880, 1620)
    }
  }
}
</script>

<style lang="scss" scoped>
  .output_image {
    max-width: 960px;
    @media screen and (max-width: 960px) {
      width: 100%;
      height: 100%;
    }
  }
</style>

<template>
  <div class="c-container">
    <header>
      <h1>{{ msg }}</h1>
    </header>
    <h3>上の段</h3>
    <div class="input_text">
      <input class="form-control" id="title_top" value="タイトル">
    </div>
    <h3>下の段</h3>
    <div class="input_text">
      <input class="form-control" id="title_bottom" value="ジェネレーターだゾ">
    </div>
    <div class="row">
      <div class="col-sm-6">
        <p>左側</p>
        <input type="text" class="form-control" id="left_cap" value="脚本 : フロント 太郎">
      </div>
      <div class="col-sm-6">
        <p>右側</p>
        <input type="text" class="form-control" id="right_cap" value="監督 : エンド 次郎">
      </div>
    </div>
    <div class="submit">
      <button type="button" class="btn btn-success" id="enter">嵐を呼ぶ!</button>
      <button type="button" class="btn btn-success" id="tweet">嵐をシェアする!</button>
      <a href="https://twitter.com/intent/tweet?&hashtags=嵐を呼ぶジェネレータ&url=https://afterschoolstudy.github.io/generator_of_call_a_storm/dist/" class="twitter-hashtag-button" data-show-count="false">Tweet #嵐を呼ぶジェネレータ</a>
    </div>
    <div class="output">
      <canvas id="output_field" width="2880" height="1620"></canvas>
      <img id="output_image" />
    </div>
    <footer>
      <p>poewred by ITCreateClub</p>
    </footer>
  </div>
</template>
<script src="https://code.jquery.com/jquery-3.3.1.min.js" integrity="sha256-FgpCb/KJQlLNfOu91ta32o/NMZxltwRo8QtmkMRdAu8=" crossorigin="anonymous"></script>
<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: '嵐を呼ぶサブタイトルジェネレータ'
    }
  }
}
$(function(){
  // 背景グラデ
  fillBack();

  $('#enter').click(function(){
    var ctx = document.getElementById("output_field").getContext("2d");
    ctx.clearRect(0, 0, 2880, 1620);
    fillBack();
    // 嵐部分
    ctx.font = '250px sans-serif';
    ctx.textAlign = 'left';
    var top_text = $('#title_top').val();
    var bottom_text = $('#title_bottom').val();
    ctx.fillStyle = '#5853A0';
    ctx.fillText(top_text,140,590);
    ctx.textAlign = 'right';
    ctx.fillText(bottom_text,2740,930);

    // 左キャプション
    var left_cap = $('#left_cap').val();
    ctx.textAlign = 'left';
    ctx.lineWidth = 5;
    ctx.fillStyle = "#FFF";
    ctx.font = "90px cursive";
    ctx.fillText(left_cap, 400, 1350);
    ctx.strokeStyle = "gray";
    ctx.strokeText(left_cap, 400, 1350);

    // 右キャプション
    var right_cap = $('#right_cap').val();
    ctx.textAlign = 'right';
    ctx.lineWidth = 5;
    ctx.fillStyle = "#FFF";
    ctx.font = "90px cursive";
    ctx.fillText(right_cap, 2480, 1350);
    ctx.strokeStyle = "gray";
    ctx.strokeText(right_cap, 2480, 1350);

    // 生成
    var ctx = document.getElementById("output_field");
    var png = ctx.toDataURL();
    document.getElementById("output_image").src = png;
    $('#output').css('border', '0');
    $('#output_field').hide();
    $('#output_image').show();
  });
});
function fillBack(){
  // 背景グラデ
  var ctx_base = document.getElementById("output_field").getContext("2d");
  ctx_base.beginPath();
  var ctx_base_color = ctx_base.createLinearGradient(0, 410, 0, 1620);
  ctx_base_color.addColorStop(0.0, '#FD81A6');
  ctx_base_color.addColorStop(1.0, '#FFFF83');
  ctx_base.fillStyle = ctx_base_color;
  ctx_base.fillRect(0, 0, 2880, 1620);
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
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
  margin: 0 auto 10px auto;
  text-align: left;
  border-bottom: 1px solid gray;
  padding-top: 20px;
  h1{
    font-size: 2rem;
  }
}
.input_text{
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
@media screen and (max-width: 960px){
  h3{
    font-size:1.4rem;
  }
}
.row{
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
.submit{
  max-width: 960px;
  margin: 0 auto 15px auto;
  text-align:right;
  #enter, #tweet {
    margin-bottom: 20px;
    width: 100%;
  }
}
#tweet{
  background-color: royalblue;
  border-color: mediumblue;
  &:hover{
    background-color: #3453b3;
  }
}
.output{
  max-width: 960px;
  height: 540px;
  margin: 0 auto 25px auto;
  border: 1px solid gray;
  @media screen and (max-width: 960px){
    width: 100%;
    height: calc( 100vw * 0.536);
  }
  #output_field{
    width: 100%;
    height: 100%;
    /*background: linear-gradient(0deg,#FFFF83,#FD81A6);*/
    font-size: 50px;
  }
  #output_image{
    max-width: 960px;
    display: none;
    @media screen and (max-width: 960px){
      width: 100%;
      height: 100%;
    }
  }
}
footer{
  height: 30px;
  border-top: 1px solid gray;
}
.c-container {
  padding: 0;
  @media screen and (max-width: 960px){
    padding: 0 20px;
  }
}
</style>

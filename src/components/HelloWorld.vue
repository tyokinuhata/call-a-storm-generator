<template>
  <div class="hello">
    <header>
      <h1>{{ msg }}</h1>
    </header>
    <h2>type your soul!</h2>
    <h3>title top</h3>
    <div class="input_text">
      <input class="form-control" id="title_top" value="はじめての">
    </div>
    <h3>title top</h3>
    <div class="input_text">
      <input class="form-control" id="title_bottom" value="懇親会LTだゾ">
    </div>
    <div class="row">
      <div class="col-sm-6">
        <input type="text" class="form-control" id="left_cap" value="脚本 : フロント 太郎">
      </div>
      <div class="col-sm-6">
        <input type="text" class="form-control" id="right_cap" value="監督 : エンド 次郎">
      </div>
    </div>
    <div class="submit">
      <button type="button" class="btn btn-success" id="enter">嵐を呼ぶ!</button>
    </div>
    <div class="submit">
      <button class="text-right btn btn-dark" onclick="location.reload();">消すゾ</button>
    </div>
    <div class="output">
      <canvas id="output_field" width="2880" height="1620"></canvas>
    </div>
    <!-- <div class="submit">
      <button type="button" class="btn btn-success" id="download">ダウンロードするゾ</button>
    </div>
    <div class="output">
      <img id="output_image" />
    </div> -->
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
      msg: 'This is Generator of Call a Storm'
    }
  }
}
$(function(){
  // var ctx = document.getElementById("output_field").getContext("2d");
  // var grad = ctx.createLinearGradient(1440,0, 1440, 1620); // グラデーションを作成
  // canvas.width = win.innerWidth;
  // canvas.height = win.innerHeight;
  // // グラデーションレイヤーに色を設定
  // grad.addColorStop(0,"#FD81A6");
  // grad.addColorStop(1,"#000");
  // ctx.fillStyle = grad; // 塗りつぶし色にグラデーションを設定
  // ctx.rect(0, 0, 0, 0);
  // ctx.fill();

  $('#enter').click(function(){
    // console.log('submit');
    var ctx = document.getElementById("output_field").getContext("2d");
    ctx.font = '250px sans-serif';
    ctx.textAlign = 'left';
    var top_text = $('#title_top').val();
    var bottom_text = $('#title_bottom').val();
    ctx.fillStyle = '#5853A0';
    ctx.fillText(top_text,140,590);
    ctx.textAlign = 'right';
    ctx.fillText(bottom_text,2650,930);

    var left_cap = $('#left_cap').val();
    ctx.textAlign = 'left';
    ctx.lineWidth = 5;
    ctx.fillStyle = "#FFF";
    ctx.font = "90px cursive";
    ctx.fillText(left_cap, 500, 1350);
    ctx.strokeStyle = "gray";
    ctx.strokeText(left_cap, 500, 1350);

    var right_cap = $('#right_cap').val();
    ctx.textAlign = 'left';
    ctx.lineWidth = 5;
    ctx.fillStyle = "#FFF";
    ctx.font = "90px cursive";
    ctx.fillText(right_cap, 1700, 1350);
    ctx.strokeStyle = "gray";
    ctx.strokeText(right_cap, 1700, 1350);
  });
  $('#download').click(function(){
    console.log('export');
    var ctx = document.getElementById("output_field");
    var png = ctx.toDataURL();
    document.getElementById("output_image").src = png;
  });
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
  border-bottom: 1px solid #000;
}
h1{
  margin:0;
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
.row{
  max-width: 960px;
  margin: 0 auto;
}
.row div{
  padding: 0;
}
.submit{
  max-width: 960px;
  margin: 0 auto;
  margin-bottom: 15px;
  text-align:right;
}
.submit #enter{
  width: 100%;
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
  background-color:#FF7FA6;
  background: linear-gradient(0deg,#FFFF83,#FD81A6);
  font-size: 50px;
}
.output #output_image{
  max-width: 960px;
}
footer{
  height: 30px;
}
</style>

<template>
  <div class="hello">
    <header>
      <h1>{{ msg }}</h1>
    </header>
    <h2>Essential Links</h2>
    <h3>title top</h3>
    <div class="input_text">
      <input class="form-control" id="title_top">
    </div>
    <h3>title top</h3>
    <div class="input_text">
      <input class="form-control" id="title_bottom">
    </div>
    <div class="output">
      <canvas id="output_field"></canvas>
    </div>
    <footer>
      <p>poewred by ITCreateClub</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'This is Generator of Call a Storm'
    }
  }
}
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
  // #5853A0
}
footer{
  height: 30px;
}
</style>

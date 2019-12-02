<template>
  <div id="app">
    <div class="grid">
      <input type="text"
             @keyup.enter="calc()"
             v-model="res" placeholder="0">
      <button class="cell num"
              @click="input(num)"
              v-for="num in numbers">{{ num }}</button>
      <button class="cell op"
              @click="input(op)"
              v-for="op in operations">{{op}}</button>
      <button class="cell op"
              @click="reset()">R</button>
      <button class="cell op"
              @click="calc()">=</button>
    </div>
  </div>
</template>

<script>


export default {
  name: 'app',
  components: {},
  data(){
    return {
      res: '',
      numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0],
      operations: ['+', '-', '*', '/']
    }
  },
  methods: {
    input(char){
      this.res = this.res.toString();
      this.res += char;
    },
    reset(){
      this.res = ''
    },
    calc(){
      this.res = eval(this.res)
    }
  }
}
</script>

<style lang="scss" scoped>
  * {
    font-family: 'Gilroy',sans-serif;
    transition: 0.3s all;
    font-weight: 600;
  }
  #app {
    width: 200px;
    box-shadow: 0 3px 15px grey;
    margin: 0 auto;
  }
  input[type="text"] {
    width: 200px;
    height: 30px;
    padding: 5px 0;
    border: 0;
    color: #243849;
    font-size: 18px;
    text-align: right;
  }
  .grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    width: 100%;

  }
  .cell {
    flex: 33%;
    height: 50px;
    font-size: 18px;
    border: none;
  }
  .num {
    background-color: #243849;
    color: #fff;
    font-weight: 400;
  }
  .cell:hover{
    background-color: #182530;
  }
  .op {
    background-color: #ff9900;
    color: #243849;
  }

</style>

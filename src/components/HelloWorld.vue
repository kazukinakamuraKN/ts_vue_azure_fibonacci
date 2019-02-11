<template>
  <div class="hello">
    <h1>{{welcomeMessage}}</h1>
    <button v-on:click="method2()">{{buttonName}}</button>
    <button v-on:click="duckReset()">Reset</button>
    <div>{{dataExample}}</div>
    <div>{{num[incrementNum]}}</div>
    <div>{{incrementNum}}</div>
    <img v-for="n in repeatBird" src="../assets/duck.png">
    <img v-for="n in repeatEgg" src="../assets/egg.png">
  </div>
</template>

<script lang='ts'>
import Vue from 'vue';
interface ComplexObjectInterface {
  testProp: string;
  modelName: number;
}
export default Vue.extend({
  props: {
    propExample: {
      type: Object as () => ComplexObjectInterface,
    },
  },
  data() {
    return {
      num: [0, 1],
      incrementNum: 0,
      repeatBird: 0,
      repeatEgg: 0,
      dataExample: 'This Property Will Be Data',
      buttonName: 'fibonacci',
      welcomeMessage: 'Welcome to Your fibonacci-bird = Vue.js + TypeScript App',
    };
  },
  methods: {
    method2() {
      if (this.incrementNum >= 1) {
        this.repeatBird = this.num[this.incrementNum];
        this.repeatEgg = this.num[this.incrementNum - 1];
        this.num[this.incrementNum + 1] = this.repeatBird + this.repeatEgg;
      }
      this.incrementNum++;
    },
    duckReset() {
      this.num = [0, 1];
      this.repeatBird = 0;
      this.repeatEgg = 0;
      this.incrementNum = 0;
    },
  },
});
</script>

<!-- Add 'scoped' attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
</style>

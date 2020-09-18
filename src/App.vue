<template>
  <!--<img alt="Vue logo" src="./assets/logo.png">-->
  <button v-on:click="showContent('bmi')">Count BMI</button><button v-on:click="showContent('bms')">Count BMS</button>
  <div v-if="bmi">
  <Bmi msg="You can calculate your Body Mass Index"/>
  </div>
  <div v-if="bms">
  <Bns msg="You can converte decimal to binary"/>
  </div>
</template>

<script>
import Bmi from './components/bmi.vue'
import Bns from './components/BNS.vue'

export default {
  name: 'App',
  components: {
    Bmi,
    Bns
  },
  data () {
    return {
      bmi: false,
      bms: false
    }
  },
    methods: {
    showContent: function (data) {
      if (data === 'bmi') {
        this.bmi = true;
        this.bms = false;
      } else {
      this.bmi = false;
      this.bms = true;
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  background-color: #4CAF50; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  border-radius: 4px;
  transition-duration: 0.4s;
  margin: 0 20px;
  width: 200px;
  outline: none;
}
button:hover {
  box-shadow: 0 12px 16px 0 rgba(0,0,0,0.24), 0 17px 50px 0 rgba(0,0,0,0.19);
  outline: none;
  cursor: pointer;
}
</style>

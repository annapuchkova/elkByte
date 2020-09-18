<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>Please enter decimal number 
    </p>
    <input v-model.number="num" placeholder="Enter number" type="number">
    <div class="results">
      <p>Binary result: {{ count(num) }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BNS',
  props: {
    msg: String
  },
  data () {
    return {
      num: null
    }
  },
  methods: {
    count: function (n) {
      return n === null || n === 0 ? '' : (+parseInt(n).toString(2));
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 10px 0;
}
.results {
  margin: 0 auto;
  width: 210px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: start;
  font-weight: bold;
}
.underweight {
  color: green;
}
.normal {
  color: blue;
}
.overweight {
  color: yellow;
}
.obesity {
  color: red;
}
input {
  width: 200px;
  padding: 10px 20px;
  margin: 0;
  box-sizing: border-box;
  border-radius: 5px;
  border: 2px solid #ccc;
  transition: border 0.6s ease-in-out;
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
  -khtml-border-radius: 5px;
}
input:focus {
  border: 2px solid green;
  outline: none
}

</style>

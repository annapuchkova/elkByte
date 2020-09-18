<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>Please enter your weigth and height using metric measures
    </p>
    <h3>Weight</h3>
    <input v-model.number="weight" placeholder="your weight" type="number">
    <h3>Height</h3>
    <input v-model.number="height" placeholder="your height">
    <h3>Your Body Mass Index</h3>
    <div class="results">
      <p>Your weight: {{ weight }}</p>
      <p>Your height: {{ height }}</p>
      <p >Your BMI: {{ countBMI }}</p>
      <p>BMI Category: <span v-bind:class="classObject">{{ showBMICategories }}</span></p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'bmi',
  props: {
    msg: String
  },
  data () {
    return {
      weight: null,
      height: null
    }
  },
  computed: {
    countBMI: function () {
      return  (this.weight !== null && this.height !== null) ? (Math.floor(this.weight / ((this.height * 0.01) * (this.height * 0.01)) * 100) / 100 ) : ''
    },
    showBMICategories: function () {
      switch (true) 
        {
          case (this.countBMI > 0 && this.countBMI < 18.5): return "Underweight";         
          case (this.countBMI > 18.5 && this.countBMI <= 25): return "Normal weight";
          case (this.countBMI > 25 && this.countBMI < 30): return "Overweight";
          case (this.countBMI >= 30): return "Obesity";

          default: return "";
        }   
    },
    classObject: function () {
      return {
        'underweight': this.countBMI > 0 && this.countBMI < 18.5,
        'normal': this.countBMI > 18.5 && this.countBMI <= 25,
        'overweight': this.countBMI > 25 && this.countBMI < 30,
        'obesity': this.countBMI >= 30
      }
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
  outline: none;
}

</style>
